---
tags:
  - Ottimizzazione
  - Ottimizzazione/PLI
---
Sia $E=\{ 1,\dots,n \}$ un insieme di $n$ oggetti.

Ad ogni oggetto $j$ si associano un profitto $P_{j}$ e un peso $w_{j}$, entrambi interi positivi.

Sia $W$ la capacità.


> [!def] Problema dello Zaino
> Consiste nello scegliere quali oggetti inserire nello zaino in modo da massimizzare il profitto, rispettando il vincolo sulla capacità.


## Definizione Formale

$x_{j}, \quad j=1,\dots,$

$$
xj=
\begin{cases}
\ 1 \qquad\quad \text{se l'oggetto }j \text{ è inserito} \\
\ 0 \qquad\quad \text{altrimenti}
\end{cases}
$$

$$
\begin{align}
max \displaystyle& \sum^n_{j_{=1}}p_{j},x_{j} \\
& \displaystyle\sum^n_{j=1}w_{j}x_{j}\leq W \\
& x_{j} \in \{ 0,1 \}
\end{align}
$$

Il problema fa parte dei problemi di riempimento.

## Problema di Riempimento

Siano $S_{1},\dots,S_{k}$ sottoinsiemi di $E$ e sia $c_{j}$ il profitto associato ad ogni $S_{j}$.

Il problema di riempimento consiste nel determinare la sottofamiglia $\mathcal{F}$ degli insiemi $S_{1},\dots,S_{k}$ che sia di profitto massimo e tale che ogni elemento di $E$ appartenga al più ad un solo sottoinsieme di $\mathcal{F}$.

$$
\begin{align}
Siano:& \\
&a_{ij}=\begin{cases}
\ 1 & & \text{se l'oggetto }i\in S_{j} \\
\ 0 & & \text{altrimenti}
\end{cases} \\
&x_{j}= \begin{cases}
\ 1 & & \text{se } S_{j} \in \mathcal{F} \\
\ 0 & & \text{altrimenti}
\end{cases} \\ \\

max \displaystyle& \sum^k_{j_{=1}}c_{j},x_{j} \\
& \displaystyle\sum^k_{j=1}a_{ij}x_{j}\leq 1 \qquad \forall\ i=1,..,n\\
& x_{j} \in \{ 0,1 \}
\end{align}
$$

## Approccio Euristico

Si costruisce una soluzione inserendo nello zaino per primi gli elementi migliori secondo un certo criterio.

Ci sono tre criteri:

1. Peso non decrescente (inseriamo molti oggetti)
2. Profitto non decrescente (inseriamo oggetti di maggior valore)
3. Rapporto profitto/peso decrescente (più efficace)

Comunque con questo approccio non si arriva all'ottimo

## Metodo (esatto) Branch and Bound per lo zaino
 
Per applicare il [[Metodo del Branch and Bound]] dobbiamo specificare:

- Come ottenere l'upper bound
- Come fare branching
- Come ottenere un lower bound

Per l'operazione di bounding adottiamo l'eliminazione del vincolo di interezza ([[Problemi di Ottimizzazione Lineare Intera#Rilassamento Lineare|RL]]|), perciò risolviamo il problema di PL:

$$
\begin{align}
max \displaystyle& \sum^n_{j_{=1}}p_{j},x_{j} \\
& \displaystyle\sum^n_{j=1}w_{j}x_{j}\leq W \\
& x_{j} \in [ 0,1 ]
\end{align}
$$

Si potrebbe usare il simplesso ma è più efficace un altro metodo.

Si sceglie il criterio di ordinamento $\dfrac{\text{profitto}}{\text{peso}}$ decrescente.


Si ordinano gli oggetti secondo questo criterio e si inizia l'inserimento. Supponiamo che si possano inserire i primi $h$ oggetti, ma non l'oggetto $h+1$

$\displaystyle\sum^h_{j=1}w_{j}x_{j}\leq W$

e

$\displaystyle\sum^h+1_{j=1}w_{j}x_{j}> W$

Inseriamo per intero i primi $h$ oggetti: $x_{1}=x_{2}=\dots =x_{h}=1$

Mentre l'oggetto $h+1$ sarà inserito frazionalmente (in parte):

$\large x_{h+1}=\dfrac{W-\text{spazio occupato}/}{P_{h+1}}=\dfrac{W-\displaystyle\sum^h_{j-1}w_{j}}{P_{h+1}}$

Lo zaino è pieno $x_{h+2}=\dots=x_{n}=0$

Il valore ottimo è $\displaystyle\sum^h_{j=1}P_{j}+P_{h+1} \dfrac{W-\displaystyle\sum^h_{j=1}w_{j}}{P_{h+1}}$

$x_{h+1}$ infatti è detta variabile critica ed è la variabile di branch, che effettua la partizione.

Un Lower Bound si ottiene considerando come Soluzione Intera Ammissibile l'arrotondamento per difetto della soluzione del $I$ rilassamento lineare $P_{0}$.


- Soluzione $P_{0}: x_{1}=\dots=x_{h}=1\qquad,\qquad x_{h+1=}\dfrac{W-\displaystyle\sum^h_{j-1}w_{j}}{P_{h+1}} \qquad,\qquad x_{h+2}=\dots=x_{n}=0$

- L'arrotondamento è: $x_{1}=\dots=x_{h}=1 \qquad,\qquad x_{h+1}=\dots=x_{n}=0$


- e il lower bound: $\displaystyle\sum^h_{j=1}P_{j}$


Come strategia si usa in genere il best bound.


> [!success] Esempio (WIP)
> 




