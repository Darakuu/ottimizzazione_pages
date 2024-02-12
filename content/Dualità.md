---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
  - Ottimizzazione/Dualita
---
# Dualità

La teoria della dualità permette di:
- Introdurre nuovi metodi risolutivi;
- Effettuare analisi di problemi di ottimalità

Dato un problema di PL detto PRIMALE, si associa ad esso un altro problema di PL detto primale:

$$
\begin{align} \\
& \text{Primale}: \\
 \\

& minC^Tx  \\
& Ax \geq b\\
& x\geq 0
\end{align}
$$

$$
\begin{align} \\
& \text{Duale}: \\
 \\

& max\ y^Tb  \\
& y^TA \leq c^T\\
& y\geq 0
\end{align}
$$

La conversione avviene secondo le regole stabilite dalla: 
- [[Tabella Primale Duale]]


> [!example]- Esempio
> ![[07-primale.png|768]]


> [!def] Problemi duali
> Una coppia di problemi duali si dice simmetrica se è del tipo:

$$
\begin{align}
& minC^Tx & \qquad & max\ y^Tb  \\
& Ax \geq b & \qquad & Ax\leq b \\
& x\geq 0 & \qquad & y\geq 0
\end{align}
$$

Se il primale è in [[Algebra della programmazione lineare#Forma Standard|Forma Standard]] si hanno problemi **asimmetrici**.

$$
\begin{align} \\
& \text{Primale } & & \\
& \text{in FS:} & & \\
 \\

& minC^Tx & \qquad & max\ y^Tb  \\
& Ax = b & \qquad & y^TA\leq c^T \\
& x\geq 0 & \qquad & 
\end{align}
$$
# Relazioni Problemi Primali-Duali

## Teorema della Dualità debole

Siano dati i problemi:

$$
\begin{align}
& & minC^Tx & \qquad & max\ y^Tb  & \\
& (P) & Ax \geq b & \qquad & y^TA\leq c^T &\qquad (D) \\
& & x\geq 0 & \qquad & y\geq 0 &
\end{align}
$$
 

E sia $x$ ammissibile per (P) e $y$ ammissibile per (D).

Allora $y^Tb\leq c^Tx$

Significato:


> [!tldr] Teorema della Dualità debole
> - La funzione obiettivo primale è un **upper bound** per il valore ottimo duale;
> - La funzione obiettivo duale è un **lower bound** per il valore ottimo primale;


> [!tldr] Corollario 1
> Se $\bar{x}$ è ammissibile per (P) e $\bar{y}$ ammissibile per (D) e $c^T\bar{x} = \bar{y}^Tb$ allora $\bar{x}$ è ottimo per (P), e $\bar{y}$ è ottimo per (D)


> [!tldr] Corollario 2: Relazione Illimitato <-> Inammissibile
> - Se (P) è illimitato $\to$ (D) è inammissibile;
> - Se (D) è illimitato $\to$ (D) è inammissibile.
 
Riassunto dei possibili casi in una tabella:

| Primale\Duale | Ottimo Finito | Illimitato | Inammissibile |
| :--: | :--: | :--: | :--: |
| Ottimo Finito | $\large\textcolor{lightgreen}{\checkmark}$ | $\large\textcolor{red}{\times}$ | $\large\textcolor{red}{\times}$ |
| Illimitato | $\large\textcolor{red}{\times}$ | $\large\textcolor{red}{\times}$ | $\large\textcolor{lightgreen}{\checkmark}$ |
| Inammissibile | $\large\textcolor{red}{\times}$ | $\large\textcolor{lightgreen}{\checkmark}$ | $\large\textcolor{lightgreen}{\checkmark}$ |
