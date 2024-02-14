---
tags:
  - Ottimizzazione
  - Ottimizzazione/PLI
---
## Branch and Bound per il problema del TSP Asimmetrico

Sia dato un grafo $G=(N,A)$ orientato, il problema del commesso viaggiatore (TSP) consiste nel determinare un [[Ciclo Hamiltoniano]] di costo minimo.

![[Ciclo Hamiltoniano]]

Quindi, assegnati dei costi agli archi, si vuole determinare il ciclo che tocchi ogni nodo di G una e una sola volta e che abbia costo minimo

## Formulazione Matematica TSP

$$
x_{ij} =
\begin{cases}
\ 1  & \text{arco }(i,j) \text{ appartiene al ciclo hamiltoniano} \\
\ 0 & \text{altrimenti}
\end{cases}
$$

$$
\begin{align}
min \displaystyle& \sum_{(i,j)\in A}c_{j}x_{j} \\
& \displaystyle\sum_{(i,v)\in A}x_{iv}=1 & \text{In ogni nodo v entra un solo arco} \\
& \displaystyle\sum_{(v,j)\in A}x_{vj}=1 & \text{Da ogni nodo v esce un solo arco} \\
& \displaystyle\sum_{i,j \in S}x_{ij}\leq |S|-1, \forall S \subseteq N, 2\leq |S|\leq |N|-1 & \text{Vincolo assenza sottocicli} \\
 \\

& x_{ij} \in \{ 0,1 \} \\
\end{align}
$$

Per applicare il [[Metodo del Branch and Bound]] al TSP dobbiamo capire, anche qui:

- Come ottenere l'upper bound
- Come fare branching
- Come ottenere un lower bound

Troviamo un lower bound, eliminando i vincoli sui sottocicli.

Così otteniamo il [[Problema dell'assegnamento]].

L'assegnamento si opera sul **grafo bipartito completo** che si ottiene duplicando i nodi di G.

Se l'assegnamento dà un ciclo hamiltoniano, abbiamo la soluzione del TSP.

Altrimenti, vuol dire che ci sono dei sottocicli $\to$ Li possiamo usare per il branching. La dimensione del branching sarà pari alla cardinalità minima dei sottocicli.

Dalla soluzione dell'assegnamento, prendiamo il sottociclo di cadinalità minima e generiamo tanti problemi quanti sono gli archi di tale sottociclo.

## Regola Generale TSP

Dato il sottociclo $((i_{1},j_{1}),(i_{2},j_{2}),\dots,(i_{k},j_{k}))$

Si generano i vincoli di branching imponendo per il primo figlio $x_{i_{1},j_{1}}$, per il secondo figlio $x_{i_{1},j_{1}}=1\ ; \ x_{i_{2}j_{2}}=0$, e così via fino al figlio k-esimo, per il quale tutti i precedenti saranno 1 e per se stesso 0.

Imporre che $x_{i_{1}j_{1}}=0$ vuol dire richiedere che nella matrice dei costi $c_{i_{1}j_{1}}=+\infty$

## Upper Bound

Si determina con l'algoritmo del nodo più vicino.

Si parte dal primo nodo e si cerca il nodo successivo connesso con costo minimo.

Esaminati tutti i nodi si trova un ciclo hamiltoniano.