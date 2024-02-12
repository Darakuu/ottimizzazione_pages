---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
  - Ottimizzazione/Simplesso
---
# Metodo delle Due Fasi

> [!question] Quando si applica?
> Il metodo delle due fasi si applica a problemi di PL con vincoli misti ($\geq,\leq,=$) nei quali non è possibile trovare come base $B$ la matrice identità.

Se non c'è la matrice identità, è impossibile avviare il simplesso infatti.


Consiste, appunto, di due fasi:

1. Determina una soluzione di base ammissibile e la forma canonica;
2. Risolvi il problema di PL.

Nella fase 1 si risolve un problema detto **Artificiale**.

Consideriamo un problema di PL in Forma Standard che non ha la sottomatrice identità:

$$
\begin{align} \\

& minC^Tx  \\
& Ax = b\\
& x\geq 0
\end{align}
$$

Aggiungiamo ad ogni vincolo una variabile $y_{i}$ detta **artificiale**.

$$
\begin{align} \\

& minC^Tx  \\
& Ax +Iy = b\\
& x\geq 0
\end{align}
$$

Nella $I$ fase si risolve il problema artificiale:

$$
\begin{align}
& min \displaystyle\sum^n_{i=1}y_{i} \\
  & a_{11}x_{1}+\dots+a_{1n}x_{n}+y_{1}=b_{1} \\
  & \vdots \\
  & a_{m_{1}}x_{1}+\dots+a_{mn}x_{n}+y_{m}=b_{m} \\
con \\
& x_{j}\geq 0,\quad y_{i}\geq 0

\end{align}

$$

Una soluzione del problema artificiale è del tipo:

- $(\bar{x},\bar{y})=(\bar{x}_{1},\dots,\bar{x}_{n},\bar{y}_{1},\dots,\bar{y}_{m})$

Se $\bar{y}_{i}=0\implies \bar{x}$ è soluzione di Base ammissibile del problema **iniziale!**

Supponiamo di aver risolto il problema della $I$ fase, per andare avanti con la teoria. 

Otterremmo:

$z^\star$=valore ottimo= $\displaystyle\sum^m_{i=1}y_{i}^\star$

A questo punto ci sono due casi:

1. $z^\star=\displaystyle\sum^m_{i=1}y_{i}^\star>0$ vuol dire che qualche $y_{i}^\star>0$ allora si conclude che il problema iniziale **non** ha soluzione ammissibile.
	   La regione ammissibile del problema è dunque vuota.
2. $z^\star=0=\displaystyle\sum^m_{i=1}y_{i}^\star=0\implies y^\star_{i}=0\  \forall\ i=1,\dots,m$
	La soluzione finale della $I$ fase $(x^\star,y^\star)=(x^\star,0)$ è tale che $x^\star$ è una soluzione di base ammissibile per il problema iniziale.


Quando si passa alla $II$ fase si usa la tabella finale della $I$ fase e si ricalcolano i costi ridotti, perché si riprende la funzione obiettivo del problema iniziale.

Ci sono 2 ulteriori sottocasi:

1. Non ci sono variabili artificiali in base.
	Si cancellano nella tabella le colonne delle variabili artificiali, e si risolve il problema.
1. Ci sono variabili artificiali in base.	
	Restano in base anche nella fase 2, e si cerca di farle uscire dalla base con il metodo del simplesso. Se non si riesce, vuol dire che il vincolo associato alle variabili artificiali in base è ridondante, e si può eliminare.



## Esempio

### Fase 1

Consideriamo un problema con soli vincoli di uguaglianza, ma senza matrice identità.

(direttamente in forma standard perché mi secco a ricopiare)

$$
\begin{align}
min(& 4x_{1}+x_{2}+x_{3}) \\
 & 2x_{1}+x_{2}+2x_{3}=4 \\
 & 3x_{1}+3x_{2}+x_{3}=3 \\
 & x_{1}-x_{2}+3x_{3}=5 \\
 & x_{j}\geq 0,\quad j=1,\dots,3
\end{align}
$$

Applichiamo la $I$ fase: creiamo un problema artificiale sostituendo la funzione obiettivo, e aggiungendo le variabili artificiali (che si comportano come variabili scarto):

$$
\begin{align}
min(& y_{1}+y_{2}+y_{3}) \\
 & 2x_{1}+x_{2}+2x_{3}+y_{1}=4  \\
 & 3x_{1}+3x_{2}+x_{3}+y_{2}=3  \\
 & x_{1}-x_{2}+3x_{3}+y_{3}=5 \\
 & x_{j}\geq 0,\quad j=1,\dots,3 \\
 & y_{i}\geq 0,\quad i=1,\dots,3
\end{align}
$$

Otteniamo la matrice:

![[05-duefasi.png|512]]


> [!warning] Nota Bene
> Se si usano le variabili artificiali in ogni riga i costi ridotti delle variabili fuori base sono dati dall'**OPPOSTO** della somma per colonna.


Calcoliamo i costi ridotti con la formula $C^T_{N}-C^T_{B}B^{-1}N$, che tradotto dal matematichese significa:
- Costo Ridotto = Coeff. Variabili nella f.o. - coeff. variabili **base** f.o. $\times$ colonna corrente.

$$
\bar{c}_{1}=0-(1,1,1)\times
\begin{pmatrix}
2 \\
3 \\
1
\end{pmatrix}
=-6
$$

 
$$
\bar{c}_{2}=0-(1,1,1)\times
\begin{pmatrix}
1 \\
3 \\
-1
\end{pmatrix}
=-3
$$

 
$$
\bar{c}_{3}=0-(1,1,1)\times
\begin{pmatrix}
2 \\
1 \\
3
\end{pmatrix}
=-6
$$

Per cui il valore corrente della f.o. è: -vettore coeff. variabili base nella f.o. $\times$ colonna termini noti:

$$
-\bar{z}= -(1,1,1)\times
\begin{pmatrix}
4 \\
3 \\
5
\end{pmatrix}
=-12
$$
 
Entra in base $x_{1}$, esce $y_{2}$.

Dopo alcune iterazioni, otteniamo la tabella finale:

![[05-duefasi2.png|512]]

Dato che $z^\star=0$, si può passare alla $II$ fase.

Notiamo che la soluzione di base trovata in questo caso è: $\left( \dfrac{1}{2},0, \dfrac{3}{2},0,0,0 \right)$, ed il vettore $\left( \dfrac{1}{2}, 0, \dfrac{3}{2} \right)$ è una SAB ammissibile per il problema iniziale.

> [!warning] Nota Bene
> La prima fase si conclude in uno dei due sottocasi:
> 1. $z^\star>0 \implies$ Problema iniziale inammissibile
> 2. $z^\star=0$ Fornisce una SAB Ammissibile per il problema iniziale (forma canonica per avviare la risoluzione del problema)

### Fase 2

Questa fase risolve il problema iniziale partendo dalla soluzione di base ammissibile trovata alla fine della prima fase: 



Notiamo che $y_{1},y_{2}$ non sono in base, e $y_{3}$ si può eliminare pure in quanto vincolo ridondante (sia colonna che riga) (è ridondante perché l'equazione che rappresenta la riga $y_{3}$ equivale a 0) 

![[06-duefasitabella.png|512]]

Ottenuta questa tabella si riprende la funzione obiettivo originale: $4x_{1}+x_{2}+x_{3}$

I valori dei costi ridotti e della funzione obiettivo sono a questo punto:

Vettore $C^T_{B}=(1,4)$

- $\bar{c}_{1}=$ 0
- $\bar{c}_{2}=$ $-\dfrac{13}{4}$
- $\bar{c}_{3}=$ 0
- $-z^\star = -\dfrac{7}{2}$

Dopo altri svariati calcoli e un'altra iterazione, arriviamo alla SAB ottima: $0, \dfrac{2}{5}, \dfrac{9}{5}$, con valore ottimo $z^\star=-\dfrac{57}{10}$

Fin 💖$\blacksquare$