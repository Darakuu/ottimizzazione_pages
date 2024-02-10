---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
---
Mettiamo in luce le proprietà geometriche della regione ammissibile.


> [!def] Iperpiano
> L'insieme delle soluzioni di un'equazione lineare in $n$ variabili.
> $\text{iperpiano }\to\ a_{1}x_{1}+a_{2}x_{2}+\dots+a_{n}x_{n}=b$


> [!def] Semispazio
> L'insieme delle soluzioni di una disequeazione lineare in n variabili.
> $\text{semispazio}\to a_{1}z_{1}+a_{2}x_{2}+\dots+a_{n}x_{n} \gtreqless b$


O, per riassumere:

| $\mathbb{R}^2$ | $\mathbb{R}^n$ |
| :--: | :--: |
| retta | iperpiano |
| semipiano | semispazi |
## Problema di PL

$$
\begin{align}
min( & c_{1}x_{1}+c_{2}x_{2}+\dots+c_{n}x_{n}) \\
& a_{11}x_{1}+\dots+a_{1n}x_{n}\gtreqqless b_{1} \\
& a_{21}x_{1}+\dots+a_{2n}x_{n}\gtreqqless b_{2} \\
& \dots \\
& a_{m1}x_{1}+\dots+a_{mn}x_{n}\gtreqqless b_{m} \\
& x_{1},\dots,x_{n} \in \mathbb{R}
\end{align}
$$
 

Sistema di equazioni e diseguazioni lineari in $n$ variabili $\to$ intersezione di iperpiani e semispazi chiusi. 



> [!def] Poliedro
> Intersezione di un numero finito di iperpiani e semispazi chiusi.
> Alias: un insieme convesso (vedi sotto)


> [!def] Combinazione convessa
> Sia $x,y \in \mathbb{R}^n$, è il punto $z=\lambda x+(1-\lambda)y$ con $\lambda \in [0,1]$
> Propria $\iff \lambda \in \ ]0,1[$ 

- La combinazione convessa di 2 punti dà il segmento che ha per estremi i due punti considerati;
- La combinazione convessa di 3 punti dà il triangolo 

> [!def] Combinazione convessa generale
> Siano $x^1,\dots,x^m \in \mathbb{R}^n$, il punto $z=\displaystyle\sum^m_{i=1}\lambda_{i}x^i$ si chiama combinazione convessa di questi punti.
> Con $\lambda_{i}\geq 0$ e la somma di tutti i $\lambda_{i}=1$


> [!def] Insieme convesso
> Un insieme $k \subseteq \mathbb{R}^n$ si dice convesso se $\forall x,y \in k$ anche il punto $z$ appartiene a $k$
> Cioè dati due punti di k, il segmento ottenuto è tutto convenuto in $k$.


> [!def] Vertice
> Un Vertice di un poliedro è un punto che **non** può essere espresso come combinazione convessa **propria** (cioè con $\lambda \in\ ]0,1[$) di altri punti del poliedro.
> Un Vertice è un estremo di un segmento $\to$ non può trovarsi "dentro" un segmento generato da altri punti.


> [!tldr] Per riassumere
> - La regione ammissibile di un problema di [[Problemi di Ottimizzazione#Programmazione Lineare|PL]] è un poliedro $\to$ è convessa;
> - I problemi di PL sono problemi convessi $\to$ Gli ottimi locali sono globali.


## Teorema Fondamentale della PL

Dato il problema:

$$
\begin{align} \\

& minC^Tx  \\
& Ax \leq b\\
& x\geq 0
\end{align}
$$

Se ha una soluzione ottima, allora esiste un vertice ottimo. 


Conseguenza: La soluzione ottima va cercata fra i vertici



> [!question] Esistono sempre vertici?
> Risulta che un poliedro ha vertici $\iff$ non contiene rette.
> C'è una **sola situazione** nella quale la regione ammissibile non ha vertici, contiene rette, e ha soluzioni ottime.

$$
\begin{align}
max(& x_{1}+x_{2}) \\
& x_{1}+x_{2}\geq 1 \\
 & x_{1}+x_{2}\leq 2
\end{align}
$$
Il poliedro è una **striscia**. 

Ci sono $\infty$ soluzioni ottime che sono tutti i punti della retta $x_{1}+x_{2}=2$, e quindi il valore ottimo della funzione obiettivo è 2.
