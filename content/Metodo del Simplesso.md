---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
---
# Preliminari al Metodo del Simplesso

## Schema Generale

1. Si sceglie un vertice
2. Se Test Ottimalità $\Large\textcolor{lightgreen}{\checkmark}$ $\implies STOP$
3. Se Test Illimitatezza $\Large\textcolor{lightgreen}{\checkmark}$ $\implies STOP$
4. Si cambia vertice altrimenti


> [!def] Forma Canonica
> Sia dato un problema di PL in forma standard, e sia B una base, il problema si dice in forma canonica se tutte le variabili di base e la funzione obiettivo son espresse in funzione delle variabili fuori base.


> [!def] Costi Ridotti
> Dato un problema di PL in forma canonica (o anche standard) rispetto alla base B, i **coefficienti** delle variabili $x_{1},\dots,x_{n}$ nella f.o. si dicono costi ridotti delle variabili rispetto alla base B



Considerando un problema in FS: 


$$
\begin{align} \\

& minC^Tx \quad & \quad & \quad min\ C^T_{B}+x_{B}+C^T_{N}x_{N}  \\
& Ax = b \quad & \quad \text{B base} \qquad & \quad Bx_{B}+Nx_{N}=b \\
& x = 0 \quad& \quad & \quad x_{B},x_{N}\geq 0  \\

\end{align}
$$

### Forma Canonica
(cioè tutto espresso in funzione di $x_{N}$)

- $Bx_{B}+Nx_{N}=b\quad\to\quad x_{B}=B^{-1}b-B^{-1}Nx_{N}$
La f.o. diventa quindi:
- $C^T_{X}=C^T_Bx_{B}+C^T_NX_{N}=C^T_{B}(B^{-1}b-B^{-1}Nx_{N})+C^T_NX_{N}=$
	- = $C^T_{B}B^{-1}b+(\underbrace{ C^T_{N}-C^T_{B}B^{-1}N }_{\text{costi ridotti var. fuori base}})x_{N} \quad\leftarrow\quad$ **f.o in forma canonica**
 

Perciò, il vettore dei costi ridotti:
- $C^T-C^T_{B}B^{-1}A$
Si partiziona in:
- $C^T_{B}-C^T_{B}B^{-1}B=C^T_{B}-C^T_{B}=0\qquad$ tutte le variabili di base, con costi ridotti nulli
- $C^T_{N}-C^T_{B}B^{-1}N\qquad$ costi ridotti delle variabili fuori base

### Test di Ottimalità

Si basa sul **segno** dei costi ridotti. Se i costi ridotti sono tutti $\geq 0$, la soluzione di base corrente è **ottima**.

Sia $x^\star=(B^{-1}b,0)$ la soluzione di base corrente. 

- $C^Tx=C^T_{B}B^{-1}b+(C^T_{N}-C^T_{B}B^{-1}N)x_{N}\geq 0$

Sappiamo che i costi ridotti delle variabili fuori base sono $\geq 0$, idem per $x_{N}\geq 0$

- $\geq C^T_{B}B^{-1}b=C^T_{B}x^\star_{B}=C^Tx^\star_{B}+C^T_{N}x^\star_{N}=C^Tx^\star$

Quindi se la f.o in base qualunque $\geq$ f.o nella soluzione di base corrente $\implies$ la soluzione di base corrente è ottima.
 


Se non vale il test di ottimalità si è costretti a cambiare vertice, passando ad un vertice adiacente. Cioè si passa a un'altra base $B'$.

$B'$ deve:
- essere adiacente (cioè differisce da $B$ per una sola colonna);
- migliorare la funzione obiettivo;
- essere tale che $x_{B'}$ è una soluzione ammissibile

In termini di **matrici** si scambia una colonna $A_{h}$ fuori base con una colonna $A_{k}$ di base.

In termini di **vettori** entra in base $x_{h}$ ed esce $x_{k}$

### Criterio di Entrata


> [!def] Criterio di Entrata
> Entra in base una variabile con costo ridotto negativo.


Supponiamo che entri in base una variabile $x_{h}$, allora la f.o. diventa:

- $C^Tx=C^T_{B}B^{-1}b+\bar{c}_{h}x_{h}$

Dove $\bar{c}_{h}$ è il costo ridotto della variabile entrata. Se la variabile entra in base, questa passa da un valore zero (dato che era fuori base) ad un valore positivo. Le altre variabili fuori base restano sempre a zero. Però ha effetto sulle variabili di base:

- $\Large\underbrace{ x_{B}=B^{-1}b }_{ \bar{b} }-\underbrace{ B^{-1}Nx_{N} }_{ \bar{A}_{N} }$

Le componenti di base dunque diventano:

$$
\begin{align}
& x_{1}=\bar{b}_{1}-\bar{a}_{1h}x_{h} \\
 & x_{2}=\hat{b}_{2}-\bar{a}_{2h}x_{h} \\
& \vdots \\
 & x_{m} = \bar{b}_{m}-\bar{a}_{mh}x_{h}
\end{align}
$$

- Se tutti gli $\bar{a}_{mh}$ sono $\geq 0$, allora $x_{h}$ può aumentare senza limiti e le $x_{i}$ sono ancora ammissibili;
- Se $x_{h}$ aumenta all'infinito la f.o. va a $-\infty$, cioè:
	- $C^Tx=C^T_{B}B^-1b-\bar{c}_{h}x_{h} \to-\infty$

Stabiliamo quindi il test di limitatezza:

### Test di Limitatezza

Se c'è un costo ridotto $\bar{c}_{h}<0$ e gli elementi $\bar{a}_{1h},\dots,\bar{a}_{mh}$ della colonna $h$ sono $\leq 0$ allora il problema **non è limitato**. 

Se non è valido il test di illimitatezza bisogna cambiare vertice. Occorre scegliere quale variabile fare uscire dalla base.

Riferendoci al sistema delle componenti di base definito prima, vogliamo che $x_{1},\dots,x_{m}\geq 0$

Otteniamo dunque:

$$
\begin{align}
& \bar{b}_{1} - \bar{a}_{1h}x_{h} \geq 0 \quad\implies \quad x_{h}\leq \dfrac{\bar{b}_{1}}{\bar{a}_{1h}} \\
& \bar{b}_{2} - \bar{a}_{2h}x_{h} \geq 0 \quad\implies \quad x_{h}\leq \dfrac{\bar{b}_{2}}{\bar{a}_{2h}}  \\
& \vdots \\
& \bar{b}_{m} - \bar{a}_{mh}x_{h} \geq 0 \quad\implies \quad x_{h}\leq \dfrac{\bar{b}_{m}}{\bar{a}_{mh}} \\

\end{align}
$$


> [!tip] Che significa?
> Tutto questo significa che $x_{h}$ può crescere fino al raggiungere il **minimo tra tutti i rapporti**. O, in altre parole:
> $x_{h}\leq\ min\left\{  \dfrac{\bar{b}_{i}}{\bar{a}_{ih}},a_{ih}>0,i=1,\dots,m  \right\}$

### Criterio di Uscita (del Rapporto)


> [!def] Criterio di Uscita
> Esce dalla base la variabile $x_{k}$ dove $k$ è l'indice cui corrisponde il minimo dei rapporti.
> $\theta= \dfrac{\bar{b}_{k}}{\bar{a}_{kh}} = min\left\{  \dfrac{\bar{b}_{i}}{\bar{a}_{ih}},a_{ih}>0,i=1,\dots,m  \right\}$

La funzione migliora del valore $|\bar{c}_{h}|\cdot \theta$, e la variabile $x_{h}$ entra con valore $\theta$.

Questo valore è infatti il valore additivo $\bar{c}_{h}x_{h}$, visto nel criterio di entrata.

# Schema del Metodo del Simplesso

Preparati, da qui in poi partono gli esempi grafici.
