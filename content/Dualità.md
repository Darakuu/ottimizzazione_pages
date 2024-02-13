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
 ![[Tabella Primale Duale]]


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


> [!def] Teorema della Dualità debole
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

## Teorema della Dualità Forte


> [!def] Teorema della dualità forte
> Se uno dei due problemi primale o duale ha ottimo finito allora anche l'altro ha ottimo finito, e i valori ottimi delle funzioni obiettivo coincidono.
> Se uno dei due problemi è illimitato, l'altro è inammissibile.

# Relazione Ottimalità Primale < - > Ammissibilità Duale

Leggi dopo aver letto: 

> [!todo]- Scarti Complementari
> ![[Scarti Complementari]]


Sia $x^\star=(B^{-1}b,0)$ la soluzione ottima primale e $y^\star$ la soluzione ottima duale.

Risulta $c^Tx^\star=y^{\star T}b$, cioè coincidono i valori ottimi.

$$
\begin{align}
c^Tx^\star & = c^T_{B}x^\star_{B}+c^T_{N}x^\star_{N} = \\
 & =c^T_{B}x^\star_{B} =\\
&=c^T_{B}B^{-1}b =   \boxed{y^{\star T}b} 

\end{align}
$$

$y^\star$ deve soddisfare i vincoli duali, cioè: $y^TA\leq c^T$

Sostituendo $y^{\star T}$ con $C^T_{B}B^{-1}$ otteniamo la dimostrazione, e arriviamo al risultato che $y^{\star T}N\leq c^T_{N} \iff c^T_{B}B^{-1}N\leq C^T_{N}\iff \underbrace{ C^T_{N}-C^T_{B}B^{-1}N }_{ \text{Costi Ridotti Var Fuori Base}}\leq 0$, che è la condizione di ottimalità primale.

**Per cui la Ottimalità Primale COINCIDE con l'Ammissibilità Duale** (importantissimo per [[Simplesso Duale]]).

### Calcolo Soluzione Duale

Possiamo usare:

1. Scarti Complementari;
2. Tabella simplesso del problema primale.

Se il problema primale ha vincolo $Ax\leq b$ si utilizzano le variabili scarto per la [[Algebra della programmazione lineare#Forma Standard|Forma Standard]].

La soluzione ottima si ottiene:

$\large \tilde{c}_{\text{iniziale}}-\bar{c}_{\text{iniziale}}$, dove:

- $\large \tilde{c}_{\text{iniziale}}:$ vettore **coefficienti** della f.o. associati alle variabili in base alla $I$ iterazione;
- $\large \bar{c}_{\text{iniziale}}:$ vettore dei **costi ridotti** nella tabella finale del simplesso associati alle variabili in base alla $I$ iterazione.


> [!success] Esempio Veloce

Dato un problema del tipo:
$$
\begin{align}
min(-2&x_{1}-x_{2}) \\
2&x_{1}\leq 2 \\
&x_{2}\leq 1 \\
 & x_{1}-3x_{2}\leq 1 \\
 & x_{1,2}\geq 0 \\
 \\
\text{In FS}: \\ \\

min(-2&x_{1}-x_{2}) \\
2&x_{1}+x_{3}= 2 \\
&x_{2}+x_{4}= 1 \\
 & x_{1}-3x_{2}+x_{5} 1 \\
 & x_{1,\dots,5}\geq 0
\end{align}
$$

Eseguendo il metodo del simplesso otterremo la soluzione ottima primale:

$(1,1,0,0,3)$ con $x_{1}^\star=1,\ x^\star_{2}=1$ e valore ottimo $f.o.=-3$

e costi ridotti finali: $(0,0,1,1,0,3)$

Calcolando la soluzione duale con la formula definita subito sopra l'esempio abbiamo:

$\text{Soluzione Duale}=(\text{coeff f.o. di }x_{3},x_{4},x_{5})-(\text{costi ridotti finali di }x_{3},x_{4},x_{5})=(0,0,0)-(1,1,0)=(-1,-1,0)$, che è la soluzione ottima duale.


> [!info] Osservazione
> Se il problema primale ha vincoli $Ax\geq b$ la soluzione ottima duale sarà la sottrazione inversa rispetto a quella appena eseguita, cioè:
> $\large \bar{c}_{\text{iniziale}}-\tilde{c}_{\text{iniziale}}$

![[Simplesso Duale]]