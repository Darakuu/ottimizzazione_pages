---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
---
# Classificazione

- Ottimizzazione Matematica: problemi con 1 solo decisore, 1 solo obiettivo
- Ottimizzazione Multiobiettivo: 1 solo decisore, tanti obiettivi
- Game Theory: problemi con tanti decisori, ognuno vuole max profitto
- Ottimizzazione stocastica: problemi con dati incerti

I problemi di ottimizzazione hanno una struttura comune: un obiettivo e delle restrizioni. 


L'obiettivo è il criterio di scelta da seguire, le restrizioni sono i vincoli o le limitazioni delle possibili scelte. 


**Ottimizzare** vuol dire la scelta migliore per soddisfare l'obiettivo, rispettando le restrizioni. 



# Ottimizzazione Matematica

Un problema di ottimizzazione è del tipo

$$
\Large

\begin{align}
& min f(x) \\
& x \in X \\
\end{align}

$$

Oppure:

$$
\Large

\begin{align}
& max f(x) \\
& x \in X \\
\end{align}
$$


Con: 
- $\large X \subseteq \mathbb{R}^n$ regione ammissibile (insieme scelte/ dei vincoli)
- $\large x \in X$ soluzione ammissibile
- $\large f:X\to \mathbb{R}$ funzione obiettivo
	- $\large f(x) = f(x_{1},x_{2},\dots,x_{n})$


Ogni problema di massimo può essere scritto come problema di minimo.