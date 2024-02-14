---
tags:
  - Ottimizzazione
  - Ottimizzazione/PLI
---
# Metodo Branch and Bound

È un metodo molto utilizzato per risolvere problemi PLI.

Si basa sul partizionamento del poliedro del (RL). Si risolvono quindi i sottoproblemi (lineari) sugli insiemi della partizione.

Dato un problema PLI:

![[Problemi di Ottimizzazione Lineare Intera#Problema PLI]]

e il suo rilassamento lineare:

![[Problemi di Ottimizzazione Lineare Intera#Rilassamento Lineare]]


Partizioniamo $X$ nei sottoinsiemi $X_{1},X_{2},\dots X_{l}$ e risolviamo:

- $\large\underset{x \in X_{k}}{min\ }c^Tx=z^k\qquad\quad k=1,\dots,l$

Il valore ottimo del problema (PLI) indicato con $z_{PLI}=\underset{k}min\ z^k$

## Procedimento

Il metodo prevede di partizionare in maniera ricorsiva $X$ e risolvere i vari sottoproblemi e i rispettivi (RL).

Si partiziona ogni partizione fino a quando si trova una sol intera o un sottoproblema risulta inammissibile.

Il metodo individua anche le partizioni sulle quali non occorre risolvere il sottoproblema.


> [!warning] Non è un metodo di enumerazione totale.


> [!success]- Esempio (Grafico, WIP)
> ![[Pasted image 20240214163352.png|512]]
> Non esploro la parte grigia


## Descrizione del Metodo

Si basa su due operazioni:

- Bounding: Si risolve un (RL) del problema di (PLI) e si ottiene un **lower bound** per il valore ottimo intero;
- Branching: La soluzione fornita dal (RL) indica come effettuare il partizionamento

Sia $x^0$ la soluzione di $P_{0}$ non intera. $x^0$ avrà qualche componente frazionaria, che chiamiamo $x^0_{h}$

Questa $x_{h}$ è detta **variabile di branch**, e genera due sottoproblemi:

$$

\begin{align}
P_{1}: & & P_{2}:\\
& minC^Tx & & minC^Tx \\
& Ax = b & & Ax\geq b\\
 & x_{h}\leq \left\lfloor {x^0_{h}} \right\rfloor  & & x_{h}\geq \left\lceil {x^0_{h}} \right\rceil \\
& x\geq 0 & & x\geq 0\\
\end{align}

$$

Se ci sono più componenti frazionarie si può:

1. Scegliere quella con parte frazionaria più vicina a $0.5$
2. Scegliere quella con coefficiente della $f.o.$ più elevato.
	- Questo rende più probabile trovare la soluzione intera nel ramo $x_{h}\leq \left\lfloor {x^0_{h}} \right\rfloor$ e chiudere invece il ramo $P_{2}$

## Criteri di Potatura

Cioè criteri per chiudere nodi. Ne esistono 3:

1. Il vincolo di branch è incompatibile con i vincoli del problema, che risulta inammissibile;
2. Si trova una soluzione intera;
3. Chiusura per bounding: si risolve un sottoproblema lineare continuo che dà una soluzione non intera e il suo valore ottimo è **peggiore** del valore ottimo corrente del problema intero


> [!info] Osservazione
> Il branching può essere binario, ma anche di dimensioni maggiori, dipende dal problema.


## Strategie di visita

### Visita in Profondità (DFS)

Si risolve il primo figlio di ogni nodo, fino a quando non si deve risalire.

Minimizza il numero di nodi aperti da esplorare, e ha bassi requisiti di memoria. Inoltre, si ottiene rapidamente una soluzione intera.

Lo svantaggio è dovuto al fatto che si possono dover risolvere molti problemi (e quindi nodi da esplorare)

### Visita per bound migliore

Si risolve prima il problema con valore ottimo migliore. Se minimizziamo, scegliamo il problema con lower bound inferiore.

In tal caso, si esplorano meno nodi, ma ne restano molti aperti. C'è maggiore richiesta di memoria, ed è possibile che se si arresta l'algoritmo prima non si trovi una soluzione intera.

Difatti, risulta più efficiente unire le due strategie:

- Si fissa il numero max di nodi aperti consentiti;
- Si applica il best bound;
- Raggiunto il limite di nodi aperti, si procede con l'esplorazione DFS.


## Upper Bound

Un upper bound per il valore ottimo del problema intero si ottiene calcolando la $f.o.$ nella prima soluzione intera disponibile.

Dato $min\{ c^Tx:Ax\geq b,x\geq 0,x \text{ intero} \}:$

| Lower Bound | Upper Bound |
| --- | --- |
|  Risolvendo i (RL) | Valore della f.o. calcolato in una sol. intera |

## Problema di Massimizzazione

$$

\begin{align}
& maxC^Tx \\ 
& \begin{rcases}
& Ax \leq b\\
& x\geq 0 \\
& \boxed{x \text{ intero}}\  \\
\end{rcases} \ X
\end{align}

$$

I (RL) forniscono degli upper bound per il valore ottimo intero.

La f.o. dà invece un lower bound

Cioè il contrario di quanto detto prima.

### Chiusura per Bounding

Come prima, se il valore ottimo ottenuto risolvendo un sottoproblema con soluzione non intera è **minore** del valore ottimo corrente si chiude il nodo.

### Esplorazione per Best Bound

Si seglie il sottoproblema con ottimo maggiore.