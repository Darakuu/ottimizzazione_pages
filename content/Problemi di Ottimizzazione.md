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


> [!def] Definizione
> **Ottimizzare** vuol dire la scelta migliore per soddisfare l'obiettivo, rispettando le restrizioni. 

## Approccio modellistico:

1. Analisi del problema e raccolta dei dati $\to$ Individuare l'obiettivo e le restrizioni;
2. Formulazione del problema $\to$ Costruzione del modello matematico: determinare le variabili, individuare l'obiettivo, esprimere i vincoli
3. Studio del modello $\to$ Esistenza delle soluzioni, unicità, etc...
4. Soluzione numerica
5. Validazione del modello

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


Ogni problema di massimo può essere scritto come problema di minimo. Risulta infatti $max\ f(x) = -min\ (-f(x)\ )$ 

## Classificazione dei problemi

**Problemi lineari**: la funzione obiettivo e i suoi vincoli sono funzioni lineari del tipo: 

$a_{1}x_{1}+a_{2}x_{2}+\dots+a_{n}x_{n}$

**Problemi non lineari:** presenza di funzioni lineari.

## Programmazione Lineare

Forma generale:

$$
\begin{align}
min( & c_{1}x_{1}+c_{2}x_{2}+\dots+c_{n}x_{n}) \\
& a_{11}x_{1}+\dots+a_{1n}x_{n}\geq b_{1} \\
& a_{21}x_{1}+\dots+a_{2n}x_{n}\geq b_{2} \\
& \dots \\
& a_{m1}x_{1}+\dots+a_{mn}x_{n}\geq b_{m} \\
& x_{1},\dots,x_{n} \in \mathbb{R}
\end{align}
$$
$x_{1},\dots,x_{n}$ Si chiamano variabili decisionali.

Valgono le ipotesi:
- Additività: si sommano i contributi delle variabili;
- Proporzionalità: ogni variabile dà un contributo proporzionale a se stessa;
- Continuità: Le variabili sono reali.