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

