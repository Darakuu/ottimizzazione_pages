---
tags:
  - Ottimizzazione
  - Ottimizzazione/PLI
---
Consideriamo il problema intero di prima:

$$

\begin{align}
& minC^Tx \\ 
& \begin{rcases}
& Ax = b\\
& x\geq 0 \\
& x \text{ intero} \\
\end{rcases} \ X
\end{align}

$$


> [!def] Taglio
> Sia $a^Tx\leq \alpha_{0}$ una disuguaglianza verificata $\forall\ x \in X$, essa si chiama **Taglio** se non è verificata dalla soluzione ottima del (RL)

![[10-taglio.png|512]]

Gli algoritmi dei piani di taglio risolvono una successione di problemi continui, ottenuti aggiungendo ogni volta un taglio, fino ad ottenre una soluzione intera.

## Schema Generale:

1. Si risolve il (RL), se $x_{RL}^{OTT}$ è intera $\implies STOP$
2. Si genera un taglio (**nuovo vincolo!**) $a^Tx\leq \alpha_{0}$
	- Tale che $a^Tx^{OTT}_{T}>a_{0}$
	- Significa: Il taglio è verificato da tutti i punti interi, ma non è soddisfatto dall'ottimo del rilassamento continuo.
3. Si risolve il nuovo problema continuo con l'aggiunta del nuovo vincolo

## Procedimento ed Efficienza

È un processo molto lungo ed estenuante da fare a mano, per questo in teoria esistono i computer, che possono operare più tagli contemporaneamente per migliorare l'efficienza, ma noi siamo studenti universitari e quindi abbiamo meno diritti delle macchine.

A seconda della scelta del taglio si hanno diversi algoritmi, ma resta comunque l'idea comune di fondo di approssimare l'involucro convesso mediante l'inserimento dei tagli.

## Implementazioni:

Una implementazione è il [[Metodo dei Tagli di Gomory]].