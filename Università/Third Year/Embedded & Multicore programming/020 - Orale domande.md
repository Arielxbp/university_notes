___

Legge di amdhal e in quali condizioni disattivare la l1 porta vantaggi su cuda

Risposta(?):La l1 ha blocchi da 128B e la l2 da 64B, se non usi i dati overfetched con la l1 attiva carichi il doppio della roba senza motivo saturando di più la banda

