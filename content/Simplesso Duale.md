---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
  - Ottimizzazione/Dualita
---
Si tratta di un metodo per risolvere il problema di PL primale nel caso in cui non sia valida l'ammissibilità primale (cioè ci sono termini noti negativi nella Forma Standard), ma sia verificata l'ammissibilità duale (cioè i costi ridotti delle variabili fuori base sono $\geq 0$).

Il metodo parte da una soluzione di base non ammissibile, cioè esterna al poliedro, e cerca di raggiungere la soluzione ottima.

Ad ogni iterazione i costi ridotti sono sempre $\geq 0$ e si cerca di avere tutti i termini noti $\geq 0$

Per riassumere:

| Simplesso Primale | Simplesso Duale |
| :--: | :--: |
| **Condizioni**: Termini Noti $\geq 0$ | **Condizioni**: C'è almeno un termine noto negativo; Costi ridotti $\geq 0$ |
| **Obiettivo**: Costi Ridotti $\geq 0$ | **Obiettivo**: Termini Noti $\geq 0$ |
## Criterio di Uscita

![[08-simplessoduale.png|512]]

Esce dalla base la variabile $x_{r}$ associata al termine noto negativo $\beta_{r}$

Si individua la riga $r$, se gli elementi della riga $r$ sono **TUTTI** $\geq 0 \implies$ **PROBLEMA PRIMALE INAMMISSIBILE** 


> [!def] Criterio di non ammissibilità
> Se il primale è inammissibile $\implies$ il duale potrebbe essere non limitato o non ammissibile. 
>
> Poichè vale la condizione di ammissibilità duale allora il problema duale non è limitato

Se ci sono elementi negativi sulla riga $\text{r-esima}$ si individua la variabile uscente $x_{s}$, dove $s$ è l'indice di colonna tale che

$\Large \dfrac{\bar{c}_{s}}{|\bar{a}_{rs}|}=min\{ \dfrac{\bar{c}_{j}}{|\bar{a}_{rj}|} : j=1,\dots,n\ ; \bar{a}_{rj}<0  \}$

## Criterio di Entrata

Resta individuato il pivot $\bar{a}_{rs}$ della trasformazione.


Riassumendo di nuovo:

| Simplesso Primale | Simplesso Duale |
| :--: | :--: |
| **Costo ridotto** $<0$ dà la variabile **entrante** | **Termine noto** $<0$ dà la variabile **uscente** |
| Criterio Rapporto per la variabile **uscente** | Criterio rapporto per la variabile entrante |
| **Criterio illimitatezza**: <br>Elementi colonna $\leq 0$ con costo ridotto negativo | **Criterio di inammissibilità:**<br>Elementi riga $\geq 0$ associati ad un termine noto $<0$ |
| **Ottimalità:**<br>Costi ridotti $\geq 0$ | **Ottimalità:**<br>Termini noti $\geq 0$ |


## Analisi di Post-Ottimalità

Supponiamo di causare la perturbazione di un termine noto $b_{r}$

$b_{r}\to b_{r}+\Delta b_{r}$

La soluzione di ottima di base è $(B^{-1}b,0)$,

Sia $\hat{b}=(b_{1},..,b_{r-1},b_{r},b_{r}+\Delta b_{r},b_{r+1},\dots,b_{m})$


> [!question] $(B^{-1}b,0)$ è ancora ottima?

<ins>Caso 1:</ins> $B^{-1}b$ ha componenti negative $\to$ Non vale l'ammissibilità primale. 

I costi ridotti $c^T_{N}-C^T_{B}B^{-1}N$ non hanno il vettore $\hat{b}$, quindi i costi ridotti sono ancora $\geq 0$

(e sono $\geq 0$ perché $(B^{-1}b,0)$ è soluzione ottima).

Possiamo applicare il simplesso duale per calcolare la nuova soluzione ottima.

<ins>Caso 2:</ins> $B^{-1}b$ ha componenti $\geq 0 \to$ è ammissibile


