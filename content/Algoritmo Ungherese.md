---
tags:
  - Ottimizzazione
  - Ottimizzazione/PLI
---
Opera sulla matrice dei costi $c_{ij}$ e trasforma la matrice dei costi in una serie di matrici equivalenti fino a determinare l'assegnamento di costo minimo che corrisponderà al ricoprimento degli zeri della matrice.

## Operazioni

1. Si sottrae ad ogni riga il suo elemento minimo: $c_{ij}=c_{ij}-\underset{j}min\ c_{ij}$ (generiamo zeri sulle righe)
2. Si sottrae ad ogni colonna il suo elemento minimo: $c_{ij}=c_{ij}-\underset{i}min\ c_{ij}$ (generiamo zeri su colonne)
3. Si cerca l'assegnamento di costo minimo, cercando il ricoprimento degli zeri della matrice. Se il numero di righe e colonne che ricoprono gli zeri è minore del numero di righe della matrice, l'assegnamento non è completo e si deve ridurre ancora la matrice. Altrimenti, si è trovato l'assegnamento completo di costo minimo
4. Si barrano le righe e le colonne che ricoprono gli zeri. Sia $\delta$ l'elemento minimo non barrato. Si aggiunge $\delta$ agli elementi barrati 2 volte (cioè l'incrocio tra riga e colonna) e si sottrae agli elementi non barrati.

Si ripetono $3$ e $4$ fino a trovare l'assegnamento completo

## Regola generale per trovare il ricoprimento minimo degli zeri

- Si etichettano le righe lasciate fuori dall'assegnamento;
- Si etichettano le colonne che hanno degli zeri in corrispondenza delle righe etichettate;
- Si etichettano le righe abbinate alle colonne etichettate dall'assegnamento ottenuto;
- Si barrano le righe non etichettate e le colonne etichettate.
