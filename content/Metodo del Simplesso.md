---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
  - Ottimizzazione/Simplesso
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
> $\theta= \dfrac{\bar{b}_{k}}{\bar{a}_{kh}} = min\left\{  \dfrac{\bar{b}_{i}}{\bar{a}_{ih}}:a_{ih}>0,i=1,\dots,m  \right\}$

La funzione migliora del valore $|\bar{c}_{h}|\cdot \theta$, e la variabile $x_{h}$ entra con valore $\theta$.

Questo valore è infatti il valore additivo $\bar{c}_{h}x_{h}$, visto nel criterio di entrata.

# Schema del Metodo del Simplesso

Preparati, da qui in poi partono gli esempi grafici.

Innanzitutto, si considera la [[Algebra della programmazione lineare#Forma Standard|Forma Standard]] del problema:

1. Si sceglie una base B (matrice $m\times m$ con Det. $\neq 0$), e si calcola la soluzione di base $x=(B^{-1}b,0)$
2. Se i costi ridotti delle variabili fuori base sono $\geq 0 \implies STOP$, la soluzione è ottima (**Test di Ottimalità**)
3. Se c'è un costo ridotto $\bar{c}_{h}<0$, quindi negativo (per il **criterio di entrata**), e gli elementi della colonna $h$ della matrice $A$ sono $\leq 0\implies STOP$, il problema non è limitato (**Test di Illimitatezza**)
4. Si calcola:
	- $\theta=min\left\{  \dfrac{\bar{b}_{i}}{\bar{a}_{ih}}:a_{ih}>0,i=1,\dots,m \right\}$ 
	- e sia $\theta$ raggiunto per $i=k$ (**Criterio di uscita**)
5. Si cambia base:
	- $B'=B \cup \{ A_{h} \}\backslash\{ A_{k} \}$ 

## Cambio Base: Operazione Pivotale

Adottiamo la forma Tableau del metodo del simplesso:

> [!example]- Tableau simplesso
> ![[Metodo del Simplesso-20240211153535519.png]]
>


Soluzione Base Ammissibile (SAB) corrente:

$\Large \underbrace{ x_{1}=\bar{b}_{1},x_{2}=\bar{b}_{2},\dots,x_{m}=\bar{b}_{m}, }_{ \text{Variabili di Base} }\quad,\quad \underbrace{ \bar{x}_{m+1}=\dots=\bar{x}_{n}=0 }_{ \text{Variabili fuori base che sono zero} }$

- Se $\bar{c}_{h}<0\implies$ entra la variabile $x_{h}$ ,
- Se il criterio di uscita ha indicato l'indice $k$, esce la variabile $x_{k}$

Dunque la colonna $A_h$ entra nella matrice di Base al posto della colonna $A_{k}$.

L'elemento $\large \bar{a}_{kh}$ si chiama $\text{PIVOT}$ o perno della trasformazione, e deve essere sempre $\neq 0$. 

La colonna h-esima si trasforma nella colonna k-esima con le seguenti operazioni:


> [!todo] Operazioni di trasformazione colonna
> 1. La riga $h$ si divide per il perno $\bar{a}_{kh}$ (motivo della condizione $\bar{a}_{kh}\neq 0$);
> 2. Alle altre righe si aggiunge un opportuno multiplo della riga $h$ del perno modificata in modo da annullare tutti gli elementi


> [!success] Esempio in LateX

$$
\begin{align}
min(& x_{1}-2x_{2}-6x_{3}) \\
 & x_{1}\leq 2 \\
 & x_{2}\leq 3 \\
 & x_{3}\leq 3 \\
 & x_{1}+x_{2}+x_{3}\leq 4 \\
 & x_{i}\geq 0,\quad i=1,2,3 \\
\end{align}
$$

Si porta il problema in forma standard

$$
\begin{align}
min(& x_{1}-2x_{2}-6x_{3}) \\
 & x_{1}+x_{4}= 2 \\
 & x_{2}+x_{5}= 3 \\
 & x_{3}+x_{6}= 3 \\
 & x_{1}+x_{2}+x_{3}+x_{7}= 4 \\
 & x_{i}\geq 0,\quad i=1,\dots,7 \\
\end{align}
$$

Abbiamo aggiunto una base B con le variabili di scarto: $x_{4},x_{5},x_{6},x_{7}$ sono variabili di base, e la matrice B in questo caso è una matrice identità. 

Questo perché se i vincoli sono tutti $\leq$ le variabili scarto diventano variabili di base.

![[Metodo del Simplesso-20240211160454386.png|512]]

La SAB Corrente sarà:
$$

SAB=
\begin{align}
\boxed{ 
 \begin{matrix}
& x_{1}=0 & x_{2}=0 & x_{3}=0 \\
& x_{4}=2 & x_{5}=3 & x_{7} = 3 & x_{7}=4
\end{matrix}
}
\end{align}
$$
- Ricordiamo che $SAB=(B^{-1}b,0)$, in notazione vettoriale, dove $B^{-1}b:$ vettore delle $m$ componenti in base, mentre $0:$ sarebbe il vettore delle $n-m$ componenti fuori base
- Se $B=I$ le componenti di base della SAB sono i termini noti.

Inoltre, se i vincoli sono tutti di tipo $\leq$ i costi ridotti coincidono con i coefficienti delle variabili della f.o. 

- Notiamo che ci sono 2 costi ridotti negativi. In questo caso, il **criterio d'entrata** sceglie quello con indice minore (cioè quello trovato prima).  Questa scelta è definita dalla [[Convergenza del Metodo#Regola di Bland|Regola di Bland]].
- Per la variabile uscente, usiamo il criterio del rapporto. In questo caso calcoliamo:
	- $\Large min\ \left\{ \dfrac{3}{1}, \dfrac{4}{1}   \right\}\implies3$
- Il rapporto minimo è pertanto in corrispondenza della seconda riga, cioè della variabile $x_{5}$, la variabile uscente.
- In sunto: **Entra** $x_{2}$, **Esce** $x_{5}$, l'incrocio tra la colonna della variabile **entrante** e la riga di quella **uscente**

![[Metodo del Simplesso-20240211161519729.png|512]]

### Operazioni sulle righe

La colonna 2 deve dividere la colonna 5.

$$
\begin{pmatrix}
0 \\
1 \\
0 \\
1
\end{pmatrix}
\ \LARGE /\ \normalsize  
\begin{pmatrix}
0 \\
1 \\
0 \\
0 \\

\end{pmatrix}
 
$$

> [!todo] Procedura

1. Il perno vale 1, quindi non ci sono modifiche da fare.
	1. Se fosse $\neq 1$, bisognerebbe dividere tutta la riga del perno per il perno stesso.
2. Operiamo sull'ultima riga, generiamo una nuova riga $R_{4}'=R_{4}-R_{2}$

$$
\begin{align}
& (1\ 1\ 1\ 0\ \quad \ 0\  0\ 1\ 4) \\
-\ & (0\ 1\ 0\ 0\ \quad \ 1\ 0\ 0\ 3) \\
\hline \\
=\ & (1\ 0\ 1\ 0\ -1\ 0\ 1\ 3)
\end{align}
$$

3. Il costo ridotto della nuova variabile di base $x_{2}$ deve fare zero: $R_{5}'=R_{5}+2R_{2}$
$$

\begin{align}
& (1\ -2\ -6\ 0\ 0\ 0\ 0\ 0) \\
+\ 2 & (0\ \quad \ 1\ \quad \ 0\ 0\ 1\ 0\ 0\ 3) \\
\hline \\
=\ & (1\ \quad \ 0\ -6\ 0\ 2\ 0\ 1\ 3)
\end{align}

$$

La nuova tabella, con relativa nuova SAB, sarà quindi:

![[Metodo del Simplesso-20240211163246611.png|512]]

$$

SAB=
\begin{align}
\boxed{ 
 \begin{matrix}
& x_{1}=0 & \textcolor{red}{x_{2}=3} & x_{3}=0 \\
& x_{4}=2 & \textcolor{red}{x_{5}=0} & x_{6} = 3 & x_{7}=4
\end{matrix}
}
\end{align}
$$

Dato che abbiamo ancora un costo ridotto negativo ($-6$), si continua con l'algoritmo.
- Entra $x_{3}$, ed esce $x_{7}$
- Si hanno le seguenti trasformazioni:
	- $R_{1}'=R_{1}$
	- $R_{2}'=R_{2}$
	- $R_{3}'=R_{3}-R_{4}$
	- $R_{5}'=R_{5}+6R_{4}$

Otteniamo un'altra tabella e nuova SAB:

![[Metodo del Simplesso-20240211164608413.png|512]]

$$

SAB=
\begin{align}
\boxed{ 
 \begin{matrix}
& x_{1}=0 & x_{2}=3 & \textcolor{red}{x_{3}=1} \\
& x_{4}=2 & x_{5}=0 & \textcolor{red}{x_{6} = 2 } & \textcolor{red}{x_{7}=0}
\end{matrix}
}
\end{align}
$$

Purtroppo dai calcoli abbiamo un nuovo costo negativo in $x_{5}$, per cui:
- Entra $x_{5}$, ed esce $x_{6}$, perché ha il rapporto minimo rispetto alla riga $x_{2}$
- E si hanno le seguenti trasformazioni:
	- $R_{1}'=R_{1}$
	- $R_{2}'=R_{2}-R_{3}$
	- $R_{4}'=R_{4}+R_{3}$
	- $R_{5}'=R_{5}+4R_{3}$
- Reminder: finora non è stato necessario toccare la riga del pivot perché abbiamo avuto fortuna e tutti i pivot sono $1$, altrimenti avremmo dovuto dividere per il pivot.

Otteniamo la tabella finale con SAB ottima:




$$

\text{SAB Ottima}=
\begin{align}
\boxed{ 
 \begin{matrix}
& x_{1}=0 & x_{2}=1 & x_{3}=3 \\
& x_{4}=2 & x_{5}=2 & x_{6} = 0 & {x_{7}=0}
\end{matrix}
}
\end{align}
$$

- Questa è la tabella finale perché tutti i costi ridotti sono $\geq 0$, quindi ci fermiamo per il Test di Ottimalità.
- Il valore ottimo della funzione obiettivo è dunque $-20$.

Questo conclude l'esempio.

- Nel caso in cui i costi ridotti siano tutti strettamente positivi ($>0$), allora per [[Convergenza del Metodo#Unicità Soluzione|Unicità della soluzione]], la SAB corrente sarebbe l'unica soluzione ottima.

# Convergenza del Metodo

Continua in:

[[Convergenza del Metodo]]

