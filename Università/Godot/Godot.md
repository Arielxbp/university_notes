___

- Pascal case for the names of the nodes

- Snake case for basically everything else

- Sprite2D is used to draw a image

- The draw order is from the root of the tree to the bottom
  ( so if node1 is under node2 in the tree, then node1 will be drawn on top of node2 )

- all of the built-in functions will have the name beginning with _

- \_\_ready() is a built-in function that is run when a Node is added to the node tree

- \_\_process() is a built-in function that is run on every frame of the game

- To target other Nodes:
```python
get_node("node path")

# or better:

$node path
```

- Vector2() is basically a list with two values, a x and a y.

- Whenever there are two parenthesis, that is a Vector

- Always multiply delta time to every movement variable when updating the movement

- $".." tells the compiler to get the parent node:
```Python
$".."
```

- Area2D is just an area that can check if another body has entered this area
  ( can be moved by changing the position )

- StaticBody2D is a static body that has NO movement
  ( like walls, obstacles and so )

- RigidBody2D is a body that moves via physics
  ( like a grenade )
  
- CharacterBody2D is a body controlled by code
  ( used by every entity that is controlled by code)

- CollisionShape should be near the center (0,0)
  ( move the sprite to allign it to the collision shape )

- Signal are used inside scripts. To create a new signal for a specific node inside a script we need to select the node that the signal starts from and insert it inside the wanted script

- Timer is a node:
  Wait Time is the length of the timer
  One Shot if true then it will run ONLY ONCE, if false then it will run continuously
  Autostart will let the timer start automatically once created
  Timer has multiple signals and the important one is the timeout()
  To start a timer inside a script we use timerName.start()

- It's possible to create custom signals.
  Built-in signals work only between nodes of the same scene
  A custom signal needs to be created inside the script of the root node of a scene
```Python
# to define a new custom signal
signal custom_signal_name

# to trigger the new custom signal (inside a func)
custom_signal_name.emit()
```

### Instantiate Scenes (using code and not the editor)
- To instantiate scenes dynamically (when in game), we need to create manually the scene.
  Then during coding:
```Python
# to preload the scene to instantiate
var name_of_scene_to_preload = preload("path of scene to preload.tscn")

# to instantiate the preloaded scene (inside a func)
var name_of_instantiated_scene = name_of_scene_to_preload.instantiate()

# to add the instantiated scene to the node tree
add_child(name_of_instantiated_scene)
```


### Randomness
- To randomize in Godot in a very simple manner:
```Python
# to get an array of the elements we want to pick randomly from
var an_array = $name_of_a_Node2D.get_children()

# to get a random element from the array using randi() % number of elements of the array for the indexing
var a_random_element = an_array[randi() % an_array.size()]
```

### Position and Global Position
- Position is a local position, it is relative to the parent.

- Global position is an exact pixel coordinate that is independent from any parent

- For example if the parent has coordinate x=100; y=200 and the child is in the same coordinate, then the child will have a local position of x=0; y=0 but a global position of x=100; y=200

### Export Keyword
- Using the export keyword on a variable we can change a variable's value declared in the script, directly from the inspector(editor)
```Python
# normal variable of type int
var speed: int = 1000

# exported variable that can be changed from the inspector
@export var speed: int = 1000
```


### RigidBody2D
- Have a gravity setting that is 1 by default (so it's affected by gravity)

- Only supposed to give this entity a starting velocity, the rest is controlled by physics


### Autocomplete for Variables
- to let the GDScript compiler give hints on variables methods or fields we need to use the as keyword when defining new variables
```Python
# to create a variables of a certain type
var a_rigid_body2D = a_rigid_body2D_Scene.instantiate() as RigidBody2D

# now using a_rigid_body2D. will give autocomplete hints
a_rigid_body2D.
```

### Camera
- It wants to be the child of the node it follows.

- Normally any camera node needs to have the position smoothing on (enabled)

- to change how much the camera sees change the zoom field
  0.1 = very big camera
  1 = default camera
  \>1 = progressively more tiny camera

### Sprite2D
- Inside the inspector, in the visibility, the modulate color will be applied to the node and its child, while the self modulate will affect only the node itself

### TileMap
- Used to draw things inside of the game

- To draw tiles on top of other tiles we need to create layers. TileMap -> Inspector -> Layers -> name of the layer and then add element.

- The order in which the tiles are drawn is similar to the tree node draw order, so the upper layer get drawn first the bottom one.

### TileSet
- It contains the graphics of a tile and

### Layers and Masks
- Every CollisionObject has a collision layer.
  Layer determines on which layer the object itself is.
  Mask determines which layers it can interact with.

### Particle nodes
- Cpu particle node is for weaker systems
- Gpu particle node is for everything else

# Shortcuts
___

- ctrl+a -> create new node
- ctrl+shift+a -> insert a scene 
- f -> center sprite on screen

- c to cancel physics layer for single block
- f to add physics layer for single block

# 2D Pixelated Sprites
___
To work with pixelated sprites change the texture filter to nearest.
This will change the rendering to a non blurry image.
![](https://i.imgur.com/q69WQWO.png)

# Animation tick
___
To change sprite fps 
![](https://i.imgur.com/brrgr6D.png)


___

a scene's root node should reflect the object's desired functionality - what the object _is_.

AnimatedSprite2D will handle the appearance and animations for our player.