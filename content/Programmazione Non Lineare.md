---
tags:
  - Ottimizzazione
  - Ottimizzazione/PNL
---
# Programmazione non lineare

Nei problemi di ottimizzazione non lineare la funzione obiettivo e/o le funzioni dei vincoli sono non lineari.
Esistono alcuni problemi non lineari che possono essere trasformati in problemi lineari

In generale però, i problemi non lineari restano tali e si affrontano con determinati metodi.
Possono essere di due tipi:

- Se $X = \mathbb{R}^n$  il problema si dice non vincolato.
- Se $X= \{ x \in \mathbb{R}^n:g_{i}(x)\leq 0,\ i=1,\dots,m;h_{j}(x)=0, j=1,\dots,p \}$ Il problema si dice vincolato:



Si pone sempre $p\leq n$, altrimenti l'insieme potrebbe risultare vuoto, oppure potrebbero esserci vincoli ridondanti.


I problemi non vincolati sono problemi in cui effettivamente l’insieme ammissibili coincide con tutto lo spazio. 

Nelle applicazioni sono considerati non vincolati i problemi con insieme ammissibile aperto. 

In tal caso infatti i punti di ottimo sono interni e possono essere caratterizzati solo dall’andamento della funzione obiettivo.

## Problemi non vincolati

Sia dato un problema di PNL non vincolata:

$$
\begin{align}
min f(x) \\
x \in \mathbb{R}^n
\end{align}
$$

Una soluzione locale $x^\star$ deve soddisfare una condizione necessaria di ottimalità. Si osserva che i punti che soddisfano una condizione necessaria di ottimalità non sono forzatamente soluzioni del problema: potrebbero ad esempio essere di max e non di minimo

![[Condizioni di Ottimalità]]

## Problemi con vincoli di uguaglianza e disuguaglianza

## Regolarità dei vincoli

![[Condizioni KKT]]