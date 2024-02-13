---
tags:
  - Ottimizzazione
  - Ottimizzazione/PLI
---
# Programmazione Lineare Intera

Consideriamo problemi del tipo:

$$
\begin{align} \\

& minC^Tx  \\
& Ax \leq b\\
& x\geq 0 \\
& \boxed{x \text{ intero}}


\end{align}
$$


> [!info] Osservazione
> La regione ammissibile di un problema intero **non è** convessa.
> In generale possono esservi alcune variabili continue e alcune intere. Si parla in tal caso di PLI mista (che non trattiamo)


> [!success]- Esempio Grafico PLI
> ![[09-pligraf.png]]

Se risolviamo il problema senza vincolo di interezza, l'ottimo sarebbe $(2.7\ ;\ 2.2)$.

Altrimenti: 

- Soluzione ottima intera: $(2;3)\quad f.o.=7$
- Soluzione arrotondata: $(2;2)\quad f.o.=6$

Come è ovvio vedere, non è possibile risolvere il problema intero eliminando il vincolo di interezza e risolvendo il problema continuo approssimando la soluzione.

Bisogna necessariamente risolvere il problema intero.

## Relazioni problemi lineari < - > interi

### Rilassamento Lineare

Dato un problema PLI (definito sopra), è possibile ottenere un **Rilassamento Lineare** (RL), o **continuo**:

$$

\begin{align}
& minC^Tx  \\
& \begin{rcases}
& Ax = b\\
& x\geq 0 \\
\end{rcases} \ P
\end{align}

$$

- Risulta che $X=P\bigcap \mathbb{Z}^n$, cioè la regione ammissibile del problema di PLI è data dalla soluzione intera del poliedro P.

- Inoltre $X\subseteq P$, cioè la reigone ammissibile del problema PLI è sempre contenuta nel poliedro P.


Si ha che il valore ottimo di (RL) è sempre $\leq$ del valore ottimo di (PLI):

- $z_{RL}\leq z_{PLI}$

Infine:

Se la soluzione ottima di (RL) è intera $\implies$ è soluzione del problema (PLI).

## Involucro Convesso

Dato un insieme discreto, esistono diversi poliedro che lo contengono. Il poliedro più interessante è l'**Involucro Convesso** (Convex Hull), e cioè il più piccolo insieme convesso che contiene i punti discreti.

L'involucro convesso ha solo vertici interi, si potrebbe quindi risolvere il problema continuo usando l'involucro convesso come insieme dei vincoli:

$$

\begin{align}
& minC^Tx & & min\ C^Tx \\ 
& \begin{rcases}
& Ax = b\\
& x\geq 0 \\
& x \text{ intero} \\
\end{rcases} \ \overset{ \text{risolviamo} }{ \longrightarrow } & & x \in conv(X)
\end{align}

$$

Il problema da risolvere è detto **Rilassamento Convessificato** e si ottiene la soluzione intera cercata.

In generale però, non è facile costruire $conv(X)$. Servono dei metodi per costruirlo.


> [!todo]- Metodo dei piani di taglio (Generico)
> ![[Metodo dei piani di taglio]]


> [!application]- Metodo di Gomory (Implementazione piani di taglio)
> ![[Metodo dei Tagli di Gomory]]
