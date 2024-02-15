---
tags:
  - Ottimizzazione/PNL
---
# Condizioni Necessarie e Sufficienti

- **Una condizione necessaria** puo servire a restringere l'insieme di punti in cui cercare la soluzione e a costruire algoritmi che soddisfano la condizione necessaria. 

- **Una condizione sufficiente** puo servire a dimostrare che un punto ottenuto per via numerica sia una soluzione ottima
## Condizione Necessaria del Primo Ordine


> [!tldr] Teorema
> Sia $x^\star$ un punto di minimo locale. Se $f$ è differenziabile in $x^\star$, allora in $\nabla f(x^\star)=0$

La condizione necessaria fornisce i punti stazionari candidati ad essere punti minimali.

Se il problema è [[Condizioni KKT#Problema Convesso|convesso]], la condizione diventa necessaria e sufficiente.

## Condizione Sufficiente del Secondo Ordine


> [!tldr] Teorema
> Sia $x^\star$ un punto di minimo locale. Se $f$ è differenziabile **due volte** in $x^\star$, allora in $\nabla f(x^\star)=0$ e la matrice hessiana $H(x^\star)$ è semidefinita positiva

## Condizione Necessaria del Secondo Ordine

Sia $x^0$ un punto interno della regione ammissibile e $\nabla f(x^0)=0$, e $f$ differenziabile due volte in $x^0$:

- Se la matrice hessiana è definita positiva, allora $x^0$ è punto di minimo locale;
- Se la matrice hessiana è definita negativa allora $x^0$ è punto di massimo locale;
- Se la matrice hessiana è indefinita, allora $x^0$ è un punto di sella
- Se la matrice hessiana è semidefinita non si può dire niente

### Regolarità dei vincoli di uguaglianza

## Condizione di Ottimalità del primo ordine

### Forma Equivalente


> [!def] Funzione Lagrangiana
> $L(x,\lambda)=f(x)+\lambda^Th(x)$



