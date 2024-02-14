---
tags:
  - Ottimizzazione
  - Ottimizzazione/PLI
---
Siano A e B due insiemi tali che $A\bigcap B=\emptyset$ e $|A|=|B|$.

Sono dati dei costi agli abbinamenti tra gli elementi di $A$ e $B$.

Il problema degli assegnamenti consiste nell'assegnare ad ogni elemento di A un solo elemento di $B$ in modo che non ci siano elementi non accoppiati e il costo totale sia minimo.

Se $|A|\neq |B|$ si aggiungono elementi fittizi e costi nulli degli abbinamenti con elementi fittizi.

## Formulazione Matematica

$x_{j}, \quad j=1,\dots,$

$$
xj=
\begin{cases}
\ 1 \qquad\quad \text{se l'oggetto }i \in A \text{ è assegnato all'oggetto} j \in B \\
\ 0 \qquad\quad \text{altrimenti}
\end{cases}
$$

$$
\begin{align}
min \displaystyle& \sum^n_{j_{=1}}c_{j},x_{j} \\
& \displaystyle\sum^n_{i=1}x_{ij}=1 \\
& \sum^n_{j=1}x_{ij}=1 \\
& x_{ij} \in \{ 0,1 \} \\ \\

& \forall i,j = 1,\dots,n
\end{align}
$$

È un particolare problema del trasporto con domanda e offerta = 1.

La matrice dei coefficienti è **Totalmente Unimodulare**

## Matrice Unimodulare


> [!def] Matrice Unimodulare
> Una matrice $A \in \mathbb{R}^{m\times x}$ si dice totalmente unimodulare quando ogni sottomatrice di ordine $P(p=1,\dots,m)$ ha determinante $\in \{ -1,0,1 \}$


> [!tldr] Proposizione
> Dato il poliedro $\{ x \in \mathbb{R}^n: Ax=b, x\geq 0 \}$ con A matrice tot. unimodulare, e b intero $\implies$ poliedro ha solo vertici interi

Possiamo quindi risolvere il problema rilassato con il vincolo $x_{ij} \in [0,1]$ (insieme agli altri vincoli diventa poi solo) $x_{ij}\geq 0$)

Non è utile usare il simplesso perché il poliedro ha vertici fortemente degeneri, si usa infatti un algoritmo specifico:

![[Algoritmo Ungherese]]


## Assegnamento su Grafo Bipartito

Il problema dell'assegnamento si può vedere su un grafo bipartito completo. Siano noti i costi $c_{ij}$ su tutti gl iarchi e si cerca un abbinamento tra gli elementi dei due insiemi di costo minimo.

![[Pasted image 20240214183550.png]]