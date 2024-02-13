---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
  - Ottimizzazione/Dualita
---
# Scarti Complementari

Siano dati i problemi primale-duale:

$$
\begin{align}
& & minC^Tx & \qquad & max\ y^Tb  & \\
& (P) & Ax \geq b & \qquad & y^TA\leq c^T &\qquad (D) \\
& & x\geq 0 & \qquad & y\geq 0 &
\end{align}
$$

Siano $\bar{x}$ ammissibile per (P) e $\bar{y}$ ammissibile per (D).

$\bar{x},\bar{y}$ sono soluzioni ottime $\iff$ soddisfano le condizioni:
- $\bar{y}^T(Ax-b)=0\leftarrow$ $m$ relazioni
- $(y^TA-c^T)\bar{x}=0\leftarrow$ $n$ relazioni

Abbiamo un sistema di $n+m$ equazioni.

## Condizioni di ottimalità (nella dualità)

$x,y \text{ sono ottimi } \iff:$

1. Ammissibilità Primale $\qquad \bar{x}:A\bar{x}=b, \bar{x}\geq 0\qquad$ Vincoli Primali
2. Ammissibiltà Duale $\qquad \quad \bar{y}:\bar{y}^TA\leq c^T,y\geq 0\quad$ Vincoli Duali
3. $c^T\bar{x}=\bar{y}^Tb$

Oppure, $\bar{x},\bar{y}$ sono ottimi $\iff$ valgono:

$\enclose{circle}{1},\enclose{circle}{2},\enclose{circle}{3}$  

e anche: 

$\enclose{circle}{4}:$ $\bar{y}^{T}(A\bar{x}-b)=0$
$\quad\ \  (\bar{y}^TA-c^T)\ \bar{x}=0$

Che significa tutto questo, e soprattutto a che serve? Capiamolo con degli esempi.

(Se stai pensando di skipparlo: è capitato non solo alle prove in itinere, ma anche durante gli orali.)

## Esempio

> [!success] Esempio (Scarti Complementari):


Un utilizzo degli scarti complementari è di calcolare la soluzione ottima duale, data la soluzione ottima primale (0,6).

Potremmo arrivarci con il simplesso o con qualsiasi altro metodo, ma l'idea è quella di **evitare di impostare l'algoritmo**

Dato il problema Primale con soluzione (0,6):

$$
\begin{align}
min(2&x_{1}-x_{2}) \\
&x_{1}+2x_{2}\geq 7 \\
2&x_{1}-x_{2}\geq-6 \\
-3&x_{1}+2x_{2}\geq 8 \\
&x_{1,2}\geq 0 
\end{align}
$$

Scriviamo il problema duale:

$$
\begin{align}
max(7&y_{1}-6y_{2}+8y_{3}) \\
 & y_{1}+2y_{2}-3y_{3}\leq 2 \\
  2&y_{1}-y_{2}+2y_{3}\leq-1 \\
 & y_{1,2,3}\geq 0
\end{align}
$$
A questo punto creiamo il sistema di scarti complementari:

Abbiamo:

- $y^T(Ax-b)=0$ con 3 equazioni in y, 
- $(y^TA-c^T)x$=0 con 2 equazioni in x.

Dobbiamo vedere quali equazioni ci danno 'informazioni' sulla soluzione duale.

**Dato che abbiamo la SOLUZIONE PRIMALE**, sostituiamo $(x_{1}=0\ ;\ x_{2}=6)$

Questo si traduce in:

$$
\begin{align}
 & y_{1}(x_{1}+2x_{2}-7)=0 \ \ \quad\qquad\to & y_{1}(0+12-7)=0 & \implies \boxed{y_{1}=0} \\
 & y_{2}(2x_{1}-x_{2}+6)=0 \ \ \quad\qquad\to & y_{2}(2-0-6+6)=0\ & \implies \boxed{\text{Non ci dà info}}\\
 & y_{3}(-3x_{1}+2x_{2}-8)=0 \ \qquad\to & -2y_{3}=0 & \implies \boxed{y_{3}=0} \\
 & x_{1}(y_{1}+2y_{2}-3y_{3}-2)=0 \quad\to & \text{NO perchè } x_{1}=0 & \implies \boxed{\text{Non ci dà info}} \\
 & x_{2}(2y_{1}-y_{2}+2y_{3}+1)=0 \quad\to& x_{2}\neq 0, \text{quindi: } \cancelto{ 0 }{ 2y_{1}C }-y_{2}+\cancelto{ 0 }{ 2y_{3} }+1=0 & \implies \boxed{y_{2}=1}
\end{align}
$$

Troviamo la soluzione duale: $(0,1,0)$.

Perciò data la funzione obiettivo duale: $7y_{1}-6y_{2}+8y_{3}$, avremo l'ottimo $7\cdot{0}-6\cdot{1}+8\cdot 0=-6$

$\text{Fin }\ \blacksquare$

Non è garantito avere un sistema così pulito. Ad esempio, nella prova in itinere dell'A.A. 2023/24 è capitato un sistema molto più complesso dove l'informazione su una variabile $y_{2}$ andava presa facendo coincidere la $y_{1}$ con la $y_{3}$. Non molto divertente. 

 