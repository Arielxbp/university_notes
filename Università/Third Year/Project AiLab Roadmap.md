
Image -> Detect features -> Write features to json/yaml -> Json + Image to model -> output 
						|
				Generate image copy

After training: Self-play -> fine-tune -> TIll good accuracy

Image -> Detect features  -> Write features to json/yaml

Image to model -> output

___


- [x] Dataset
- [x] Feature extractor
- [x] StreetCLIP remove last heads
- [x] Train feature + corresponding image + corresponding coordinates and country
- [x] Compare 


# Notes

## config.py

Inizializzazione delle variabili costanti usate all'interno del progetto

## dataset.py

funzione gather_samples:  Restituisce una lista di tuple (immagine, json) prese dal dataset

classe CountryEncoder:  Individuare tutti i paesi presenti del dataset e assegnare un idx 

funzione parse_metadata: dato un json di un immagine, si ricava i metadata dell'immagine, quindi coordinate e paese dell'immagine

PIL_AUG_TRANSFORM: Un T.Compose usato per la fase di trasformazione delle immagini in varianti non troppo differenti ma che aumentano il dataset.

TENSOR_AUG_TRANSFORM: Un T.Compose usato sui tensor per blurrare le varianti

BASE_TRANSFORM: Un T.Compose usato per trasformare le immagini in input, ridimensionandole in 336x336, conversione in tensors, e normalizzandole rispetto alle statistiche di CLIP. Questa trasformazione viene fatta su tutte le immagini, anche le varianti.

classe GeoSampleDataset: Effettua tutte le trasformazioni sopra definite sul dataset. Restituendo un dizionario (immagine in tensor, path, coordinate in tensor, paese, varianti)

funzione create_dataset: chiama gather_samples, poi costruisce CountryEncoder, poi GeoSampleDataset. Quindi usato per inizializzare tutto il dataset da usare.

funzione split_dataset: Gestisce lo splitting del dataset da usare tra training e validazione. Di default usa come split 85/15 training

## eval.py

funzione \_centroid_cache_path: Genera un filename unico tramite hash per salvare il centroid.pt. Così modelli differenti non usano lo stesso centroid.pt

funzione load_model: Istanzia StreetCLIPFusion con il backbone non freezato. Carica il modello best_model.pt, lo mette sul device(gpu) e lo mette in modalità valutazione (evaluation)

torch_no_grad decoratore usato durante valutazione e/o inferenza per velocizzare la computazione e diminuire la memoria usata durante questi.

funzione compute_country_centroids: Costruisce un vettore embedding per paese. Se esiste già il centroid.pt allora lo carica, altrimenti computa per ogni paese usando 200 campioni immagine il centroid tensor di ogni paese.

funzione evaluate: Data un'immagine in input, computa la similarità del coseno con tutti i centroid tramite matmul, e prende la top 5 dei paesi.

funzione predict_single: Effettua l'inferenza di una singola immagine data in input, carica e preprocessa l'immagine con il BASE_TRANSFORM, lo passa attraverso il modello, fa matmul control la matrice dei centroids, e prende la top 5

## features.py

classe FeatureExtractor: è una interfaccia (classe astratta) che definisce le funzioni di estrazione di feature da un'immagine

classe GroundingDINOExtractor: Estrattore di feature stradali usando grounding dino in modalità zero shot detection di oggetti

classe YOLOWorldExtractor: Estrattore di feature stradali usando Yolo world usando modello locale yolov8.pt e detecta le feature dell'immagine in un vettore di confidence di 55 dimensioni riguardo agli oggetti riconosciuti

classe CLIPBasedVegetationExtractor: Estrattore di feature di vegetazione usando CLIP, sempre 55 dimensionale vettore di probabilità con somma 1.

classe CompositeFeatureExtractor: Wrapper che mette insieme l'estrattore dei feature stradali con quello della vegetazione in un'unica api.

## model.py

classe ProjectionHead: È un MLP a due layer con LayerNorm + ReLU in mezzo. (Linear(input_dim, hidden_dim) → LayerNorm → ReLU → Linear(hidden_dim, output_dim)). Usato sia per road projection che per vegetation projection. No dropout e no activation on output (identity)

classe StreetCLIPFusion: Il cuore del modello, Fonde StreetCLIP visual embeddings con i vettori delle feature stradali e della vegetazione in un unico 512-dim L2 embedding normalizzato.
Mantiene solamente il vision model e il visual projection, il resto di clip viene scartato.
Congela il backbone, crea obj_projection e veg_projection, due istanze di projectionHead (classe sopra descritta) e infine crea il fusion_head, ovvero un MLP a 3 layer:
```
Linear(1280, 1024) → LayerNorm → ReLU → Dropout(0.1)
→ Linear(1024, 512) → LayerNorm → ReLU → Dropout(0.1)
→ Linear(512, 512)
```

classe ConstrastiveLoss: serve per supervisionare le perdite (loss). Usato quando --no-plonkit è true.

classe MultiModalConstrativeLoss: è usato di default durante il training per le perdite. Ogni embedding di un immagine (che include road+veg projections) viene pullato verso il text embedding del paese corrispondente. I gradients flow through obj_projection, veg_projection e fusion_head.

## precompute.py

funzione precompute_embeddings: precomputazione degli embeddings di streetCLIP per tutto il dataset.

funzione precompute_features: precomputazione delle feature usando yoloworld e clip per tutto il dataset.

In modo tale la precomputazione viene fatta una sola volta, e il training posso finetunarlo quanto voglio tanto non ci mette così tanto tempo in quanto usa sempre le stresse cose precomputate

## train.py

classe PrecomputedDataset: carica gli embeddings e le features precomputate dagli shard invece di eseguire il modello durante il training.

funzione get_linear_warmup_scheduler: restituisce un LambdaLR scheduler con: fase 1 linear ramp da 0 a base_lr e fase 2 coseno decary da base_lr a 0

funzione train_epoch_plonkit: è il training loop che si usa con la modalità plonkit (cioè MultiModalConstrativeLoss). Per ogni batch, estrae embeddings, features, text embeddings e labels, computa MultiModalConstrativeLoss, scala il loss per 1/ gradient_accumulation_steps, chiama backward(). Ogni gradient_accumulation_steps, clips grads, steps optimizer, steps scheduler, zeros grands, e restituisce l'average loss durante l'epoch.

funzione train: è la funzione di training principale, carica gli samples, costruisce CountryEncoder, splitta gli indici in 85/15, fa il setup di plonkit, crea il dataset usando i dati precomputati, crea il modello streetCLIPFusion, ottimizza il modello usando AdamW solo sui parametri trainabili (non freezati), seleziona MultiModalConstrastiveLoss + train_epoch_plonkit, lo scheduler fa linear warmup + coseno decay sui steps totali, quindi esegue il training loop di 10 epoch, e infine restituisce il modello trainato.

___

# Explanation

## MLP

A multilayer Perceptron 

## Embeddings

An embedding, or embedding vector, is a mathematical projection of high dimensional inputs into a lower dimensional vector space.

This vector space is specifically structured so that geometric proximity correlates with semantic or spatial similarity

For example, in a specific embedding space, the vector representation for the phrase "red car" will be located near the embeddings for images of "red cars", while being positioned far away from unrelated concepts like "snowy mountain".

## Projections

A projection is a mathematical transformation used to map data from its original representation into a different dimensional space, allowing a neural network to properly process, compare, or extract features from that data.

## Head

A head refers to the to the task-specific __layers__ appended to the output of a model's backbone.

While the backbone acts as a general-purpose engine to extract feature representations from raw data, the head is the one responsible for transforming those features into specific downstream predictions.

This modular decoupling, splitting the network into backbone and head, is highly efficient while designing a system. It allows to keep large computationally expensive pretrained backbone __frozen__ while simply swapping out custom lightweight head to adapt the model.

## Constrastive loss (and Multi modal contrastive loss)

Contrastive loss is a mathematical training objective that encourages a model to map semantically similar (positive) samples close together in a shared embedding space, while simultaneously pushing dissimilar (negative) samples far apart.

Instead of relying on explicit class labels, it turns data matching into a classification problem.

The model computes the similarity (typically cosine similarity) between an __anchor__ and a positive sample, maximizing this score while minimizing its similarity against all other mismatched, negative samples in a training batch.

__Multi modal__ constrastive loss extends this concept to align fundamentally different data types, such as images, text and gps coordinates, within the exact same shared, continuous embedding space. By applying this __bidirectional__ (symmetrical) cross-entropy loss, the model learns a __joint__ representation where an image of a dog naturally aligns with the text phrase "a photo of a dog" without ever being explicitly trained on a "dog" category label.

In the project multi modal constrastive loss is used to align street-view imagery with geographical text. So the model utilizes this to:
- Compare these fused visual embeddings against country-level text descriptions scraped from Plonkit.

Both the fused image embeddings and the Plonkit text embeddings are L2-normalized, and a symmetric contrastive loss is applied to both (image to text and text to image). This trains the model to mathematically map a raw street-view panorama directly to the descriptive text profile of its correct country.

Also the symmetric cross entropy loss is scaled by a learnable temperature parameter.

## LayerNorm, Dropout, loss, ReLU, Linear

Layer normalization is a technique used to stabilize gradient flow and accelerate network training by ensuring values are on a similar scale.

Rectified Linear Unit (ReLU) is a non-linear activation function. It introduces non-linearity to the network, allowing it to learn complex patterns.

Dropout is a stochastic regularization technique used to prevent models from overfitting or memorizing training data. During training, it randomly sets a fraction of a layer's activation to zero. This prevents the network from relying too heavily on any single neuron and forces it to learn robust, redundant representations.

Loss (or cost) is the mathematical objective function that measures how far off the model's predictions are from the true targets. During training, optimization algorithms minimize this loss value to update the model's parameters via backpropagation. Examples include cross entropy loss.

Penguin uses structured feature streams for road and vegetation features. To process these streams, penguin uses a generic 2-layer multilayer perceptron called a __projectionHead__. This head explicitly combines these components in the sequence:
- Linear(in, hidden) -> LayerNorm(hidden) -> ReLU -> Linear(hidden, out).
The object projection head maps 44-dimensional features to a 512-dimensional hidden state, normalizes it, applies the ReLU activation, and linearly projects it to 256 dimensions.

Penguin uses a learnable text projection consisting of a Linear(768 -> 512) mapping followed by a LayerNorm(512) to ensure the text embeddings align properly with the fusion output space.

Penguin does not list a dropout layer among its operations.

## AdamW

Penguin uses AdamW __optimizer__ to update its weights during training. It pairs this optimizer with a linear warmup and cosine decay learning rate schedule, a learning rate of 1e-4 and a weight decay of 0.01.

AdamW is an influential optimization algorithm in deep learning that improves upon the standard Adam optimizer by __decoupling__ weight decay from gradient-based parameter updates.

## Linear Warmup & Cosine-decay

These are a learning rate schedule for training.

It ensure stable model convergence.

This schedule dictates how the model's learning rate changes over the course of training.

At the very beginning of training, the learning rate starts at a minimum value and is linearly increased. In penguin this warmup phase is configured to last for exactly 500 steps, this gradual increase prevents the adaptive optimizer (AdamW) from making erratic, destabilizing parameter updates during the early stages of training when its running moment estimates are still innacurate.

Cosine decay: Once the 500 warmup steps are complete and the learning rate has hit its peak, it begins to smoothly decrease following the shape of a cosine curve until it reaches a minimum target value. This gradual curved decay __helps the model stabilize__ its parameter trajectories, allowing it to fine-tune its weights and settle into an optimal minimum as the training process apporaches completion.

## Gradient (Gradient flow and gradient accumulation)

Gradients represent the __slope__ or the vector of partial derivates of the model's loss function with respoect to its learnable parameters.
Because gradients point in the direction of the steepest increase in loss, optimization algorithms adjust the model's weights in the exact opposite direction to minimize the error and improve predictions.

Gradient flow refers to how effectively these gradients are transmitted backward through the layers of the network during the backpropagation phase.

Gradient accumulation is a memory-saving technique used to simulate training with a very large batch size when physical GPU memory is limited.

In penguin these optimization mechianics are strictly managed to train the model to accurately predict a photo.
Penguin calculates gradients based on its contrastive loss objectives (the multi modal contrastive loss), which evaluates how well the fused street-view images align with their corresponding country text embeddings from plonkit.
The AdamW optimizer then uses these gradients to update the trainable parameters.
Penguin utilizes `LayerNorm` and `ReLU` activations within its generic 2-layer MLP `ProjectionHead` (which processes the 44-dimensional object and 63-dimensional vegetation features). `LayerNorm` helps maintain a stable gradient flow by normalizing inputs across the feature dimension, while `ReLU` mitigates the vanishing gradient problem by maintaining a constant gradient of 1 for all positive inputs.

Constrastive learning HEAVILY relies on large batch sizes for the model to learn. But GPU memory is little -> penguin uses gradient accumulation -> base batch\_size = 32 configured with gradient\_accumulation\_steps = 4. So this allows the model to simulate a larger effective batch size of 128 before triggering an optimizer weight update.

Gradient clipping, if accumulated gradients exceed the set threshold (MAX_GRAD_NORM=1.0) then the gradients are scaled down, this acts as a safeguard, ensuring the AdamW optimizer does not make erratic updates.

## Weights

Weights are the learnable parameters that the model adjust during training to make accurate predictions.

During the training process, optimization algorithms (AdamW) use gradients to update these weights incrementally, minimizing the errors (or loss) of the model's predictions.

## Model

A model consists of two distinct components:
- The architecture
- The weights

The architecture defines the specific sequence of operations, how many layers exist, what types of layers they are, what activation functions (like ReLU) are applied. The architecture does not contain any learned knowledge, it just provides the mathematical pathways and capacity for the system to learn.

The weigths and biases are the actual numerical values the network has optimized during training to make accurate predictions.

To actually run a model, these two must be combined.