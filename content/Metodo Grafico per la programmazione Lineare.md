---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
---

> [!tip] Rette nel piano
> Una retta ha un'espressione del tipo $a_{1}x_{1}+a_{2}x_{2}=c$
> $(a_{1},a_{2})^T$ è un vettore ortogonale alla retta appena definita, che punta verso il semipiano $a_{1}x_{1}+a_{2}x_{2}\geq c$
> Trasposto perché i vettori sono sempre in colonna.

I problemi di programmazione lineari in 2 variabili possono essere risolti graficamente.

# Metodo Grafico

Si basa sulla rappresentazione geometrica della regione ammissibile e della funzione obiettivo. 

Nei problemi di PL i vincoli sono disequazioni lineari $\to$ quindi semipiani.

$$
\begin{align}
max( & 20x_{1}+15x_{2}) \\
& 2x_{1}+2x_{2}\leq 8 \\
& 2x_{1} + x_{2} \leq 6 \\
& x_{1},x_{2} \geq 0
\end{align}
$$
Ponendo i vincoli in forma di retta, otteniamo il grafico:

![[Metodo Grafico per la programmazione Lineare-20240210005449968.png|512]]


> [!tip] Come scegliere il semipiano giusto
> Si prende il punto test $(0,0)*$ e si sostituisce in $2x_{1}+2x_{2}\leq 8$, difatti in questo caso si ottiene $0\leq 8$, che è vero.
> Il semipiano giusto in questo caso è quello che contiene il punto test.

