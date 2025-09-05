___

Java Swing è un evoluzione di AWT

In Swing ci sono due elementi principali:

- Components
- Containers

#  Components
___

- Sono oggetti grafici che offrono interazioni con l'utente come i pulsanti o le caselle di testo

- JButton
- JLabel
- JTextField

# Containers
___

- Contengono i Components
- Hanno il compito di posizionarli e dimensionarli in base al Layout Manager che è stato a loro assegnato

- JFrame, JDialog

- JPanel




# JFrame
___
```Java
JFrame frame = new JFrame("title") 
// costruisce la finestra con un titolo da inserire opzionale
```

- Meglio estendere JFrame in un altra classe e non nel main, e lì implementare la finestra

## .setDefaultCloseOperation

Usato per decidere cosa succede quando si clicca X sulla finestra
Usato sulla variabile di tipo JFrame, da passare in input al metodo:

- JFrame.DO_NOTHING_ON_CLOSE
- JFrame.HIDE_ON_CLOSE
- JFrame.DISPOSE_ON_CLOSE
- JFrame.EXIT_ON_CLOSE

## .setSize

Usato per impostare una grandezza della finestra:
```Java
int larghezza; // in pixel 
int altezza; // in pixel
frame.setSize(larghezza, altezza);
```

## setLocationRelativeTo

Usato per impostare la posizione della finestra al centro dello schermo:
```Java
frame.setLocationRelativeTo(null)
```
Se viene passato null, la finestra viene posizionata al centro

## setLocation

Usato per impostare la posizione della finestra in x y dello schermo

## setResizable

Usato per settare se ingrandibile la finestra

## setVisible

Usato per settare se la finestra è visibile o meno
Scriverlo sempre DOPO aver impostato i settings della finestra

# Layout Manager
___

- posiziona i componenti correttamente all'interno della finestra e dare a ogni componente le dimensioni corrette

- si occupa di spostare i componenti se viene ridimensionata la finestra

- 