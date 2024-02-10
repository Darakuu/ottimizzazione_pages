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

Si basa sulla rappresentazione geometrica della regione ammissibile, dei vincoli e della funzione obiettivo sul piano cartesiano. 

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

E difatti la soluzione ottima sarà il punto $(2,2)$

> [!tip] Come scegliere il semipiano giusto
> Si prende il punto test $(0,0)*$ e si sostituisce in $2x_{1}+2x_{2}\leq 8$, difatti in questo caso si ottiene $0\leq 8$, che è vero.
> Il semipiano giusto in questo caso è quello che contiene il punto test.

> [!info] Osservazione
> Se i coefficienti della funzione obiettivo non sono tutti nulli, la soluzione non è mai interna alla regione ammissibile.
> Quindi starà sul bordo.

Un'altra procedura è quella di considerare il fascio di rette generato dalle rette parallele e ortogonali a quella che rappresenta la funzione obiettivo, cioè quindi al vettore $(20,15)^T$ nell'esempio, in direzione dei valori crescenti di $k$.

![[Metodo Grafico per la programmazione Lineare-20240210010954218.png]]

La soluzione ottima sarà l'ultimo punto ammissibile comune con la retta del fascio.


> [!todo] Procedura
> 1. Rappresentiamo i semipiani di vincoli sul piano cartesiano;
> 2. Per rappresentare la funzione obiettivo, tracciamo le linee di livello della f.o. , cioé il fascio di rette $c_{1}x_{1}+\dots+c_{n}x_{n}=k$ al variare di k.
> 3. Le linee di livello sono parallele tra loro e ortogonali al vettore $(c_{1},c_{2},\dots,c_{n})^T$. $k$ è il valore della f.o che dobbiamo max/minimizzare.
> 	1. Per massimizzare: trasliamo la retta della f.o. seguento la direzione del vettore.
> 	2. Per minimizzare: andiamo in direzione opposta.
> 4. Fra tutte le linee di livello prendiamo quella che ha il valore max (min) di k e si ottiene la soluzione prendendo l'ultimo punto comune tra la retta del fascio e la regione ammissibile
