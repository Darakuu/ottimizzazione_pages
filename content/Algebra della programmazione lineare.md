---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
---
Cerchiamo di esprimere il concetto di vertice in modo algebrico, sfruttando la struttura di vincolo.

# Forma Standard

Si dice Forma Standard di un problema di PL, il problema scritto nella forma:

$$
\begin{align}
 min  & \displaystyle\sum^n_{j=1}c_{j}x_{j} \quad & \quad & \qquad min\  C^Tx \\
 & \displaystyle\sum^n_{j=1}a_{ij}x_{j}=b_{i}, & \qquad i=1,\dots,n & \qquad Ax=b \\
 & x_{j} \geq 0, \qquad& j=1,\dots,n & \qquad x\geq 0
\end{align}
$$

con $b_{i}\geq 0$

## Caratteristiche:

1. Problema di minimo;
2. Vincoli di **uguaglianza**;
3. Termini noti $b_{i}\geq 0$
4. Variabili $x_{j}\geq 0$

Ogni problema di PL può essere scritto in FS.

## Regole di conversione

- Un problema di max si scrive come problema di min:
	- $max(3x_{1}+7x_{2})\quad\overset{\text{risolvo}}{ \implies }\quad min(-3x_{1}-7x_{2}) \quad\implies\quad -min(3x_{1}-7x_{2})$
- Vincolo di $\leq$ si trasforma in vincolo di $=$ aggiungendo una variabile di SCARTO (SLACK) $+\ x_{n+1}$
	- $4x_{1}+5x_{2}\leq 12 \implies 4x_{1}+5x_{2}+\textcolor{red}{x_{3}}=12$
- Vincolo di $\geq$ si trasforma in vincolo di $=$ sottraendo una variabile di SURPLUS $-x_{n+1}$
	- $4x_{1}+5x_{2}\geq 12 \implies 4x_{1}+5x_{2}\textcolor{red}{-x_{3}}=12$
- Variabile $x_{j}\leq 0$, Si moltiplica per -1 e si rinomina:
	- $x_{j}\leq 0 \implies -x_{j}\geq 0 \implies \hat{x}_{j}=-x_{j}$
	- $x_{j}$ si sostituisce in tutti i vincoli e nella f.o.
- Variabile $x_{j}$ libera in segno, si introducono due variabili $x_{j}'\ ;\ x_{j}''\geq 0$, e si pone $x_{j}=x'_{j}-x''_{j}$, e poi si sostituisce la variabile.

# Forma Standard e Vertici

Partendo da un esempio, consideriamo il poliedro:

$$
\begin{align} \\
 & x_{1}+2x_{2}\leq 10  &  & \qquad x_{1}+2x_{2}+x_{3}=10 \\
 & 2x_{1}-3x_{2}\leq 6  & \overset{\text{FS}}{\implies} &\qquad 2x_{1}-3x_{2}+x_{4}=6   \\
 & x_{1}+x_{2}\leq 9  &  &\qquad x_{1}+x_{2}+x_{5}=9 \\
 & x_{1},x_{2}\geq 0 &  & \qquad x_{i}\geq 0, \quad i=1,\dots,5
\end{align}
$$

Se poniamo $x_{1}=x_{2}=0$ Troviamo la soluzione $(0,0,10,6,9)$, le componenti sono $\geq 0\implies$ è un vertice.

Generalizzando l'esempio, consideriamo: 


$$
\begin{align} \\

& minC^Tx  \\
& Ax \leq b\\
& x\geq 0
\end{align}
$$

con:
- $\large x \in \mathbb{R}^{m+n}$
- $\large b \in \mathbb{R}^m$
- $\large \text{rango(A)}=m$

E richiediamo che $m<n$.


> [!question]- Perché?
> - Se $m=n$ vuol dire che il sistema $Ax=b$ ha un'unica soluzione, cioè nella regione ammissibile c'è un solo punto, e quindi non c'è alcuna ottimizzazione da effettuare, non avendo alcuna altra scelta.
> - Se $m>n$ vuol dire che ci sono dei vincoli in eccesso, ridondanti.


## Per trovare i vertici...

- Annulliamo n-m variabili;
- Risolviamo il sistema nelle rimanenti variabili;
- Se le variabili sono tutte $\geq 0$, abbiamo un vertice.

Dobbiamo però capire come scegliere le variabili da annullare.


> [!def] Base Vettoriale
> Data una matrice $A \in \mathbb{R}^{m+n}$ una base $B$ è una sottomatrice di $A$ formata da $m$ colonne linearmente indipendenti.

Se $\text{rango(A)}=m \implies \text{esistono basi di\ } B$.

Individuata una base B, la matrice si partiziona:

$$ 

A =
\begin{array}{cccc:ccc}
a_{11} & a_{12} & \dots & a_{1m} & a_{1m+1} & \dots & a_{1n}\\ 
a_{22} & a_{22} & \dots & a_{2m} & a_{2m+1} & \dots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2}  & \dots  & a_{mm} &  a_{mm+1} & \dots & a_{mn} \\
\end{array}

$$


Supponiamo che la matrice B sia fatta con le prime $m$ colonne di $A$. 

Difatti, $B$ è quadrata: $B \in\mathbb{R}^{m+m}$, le altre colonne di $A$ formano la matrice **non di base** $N\in\mathbb{R}^{m+(n-m)}$. 


La matrice $A=[B,N]$ si partiziona quindi in $B$ e $N$, ed anche il vettore $x$ si partiziona in:
$x=(x_{B},x_{N})$:
- $x_{B}=$ componenti associate alla colonna di $B$;
- $x_{N}=$ componenti associate alla colonna di $N$

Il sistema $Ax=b$ allora si scrive:

- $Bx_{B}+Nx_{N}=b$
- $x_{B}=B^{-1}b-B^{-1}Nx_{N}$

La matrice B è invertibile, perché composta da colonne linearmente indipendenti. Per questo possiamo moltiplicare a sinistra per $B^{-1}$



Per trovare un vertice la scelta naturale è porre $x_{1}=x_{2}=0$, cioè porre a zero le **variabili fuori base**. 


> [!def] Soluzione di Base
> Dato il sistema $Bx_{B}+Nx_{N}=b$ si dice **soluzione di base** il vettore $x=(B^{-1}b,0)$, cioè $x_{B}=B^{-1}b$ e $x_{N}=0$
> (Componenti di base sono date da $B^{-1}b$ e quelle fuori base sono nulle).


- Se $x_{B}\geq 0$ la soluzione di base si dice **ammissibile**.
- Se qualche componente di base è nulla, si dice **degenere**


> [!tldr] Teorema 1
> Dato il poliedro $P=\{ x \in X: Ax=b,x\geq 0 \}$
> $x \in P$ è un vertice se e solo se è una soluzione di base ammissibile

- Per il [[Geometria della programmazione lineare#Teorema Fondamentale della PL|Teorema Fondamentale della PL]] $\implies$ bisogna cercare l'ottimo tra i vertici;
- Per il Teorema 1 appena definito $\implies$ bisogna cerca l'ottimo tra le soluzioni di base ammissibile.


> [!question] Quante soluzioni di base ammissibile ci sono?
> Il numero di sol di base è legato al numero di basi B.
> Possiamo estrarre da A $\binom{n}{m}$ sottomatrici di ordine m.
> Fra queste sottomatrici, ve ne sono alcune non invertibili, e alcune che generano soluzioni di base non ammissibile.
> Quindi, il numero di soluzioni di base è al più $\boxed{\binom{n}{m}}$

Questa è la base del [[Metodo del Simplesso]]



