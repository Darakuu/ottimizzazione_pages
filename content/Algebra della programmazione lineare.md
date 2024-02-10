---
tags:
  - Ottimizzazione
  - Ottimizzazione/ProgLineare
  - Algoritmi/SecondaProva
---
Cerchiamo di esprimere il concetto di vertice in modo algebrico, sfruttando la struttura di vincolo.

# Forma Standard

Si dice Forma Standard di un problema di PL, il problema scritto nella forma:

$$
\begin{align}
 min  & \displaystyle\sum^n_{j=1}c_{j}x_{j} \quad & \quad & \qquad min\  C^Tx \\
 & \displaystyle\sum^n_{j=1}a_{ij}x_{j}=b_{i}, & \qquad i=1,\dots,n & \qquad Ax=b \\
 & x_{j} \geq 0, \qquad& j=1,\dots,n & \qquad x\geq 0
\end{align}
$$

con $b_{i}\geq 0$

## Caratteristiche:

1. Problema di minimo;
2. Vincoli di **uguaglianza**;
3. Termini noti $b_{i}\geq 0$
4. Variabili $x_{j}\geq 0$

Ogni problema di PL può essere scritto in FS.

## Regole di conversione

- Un problema di max si scrive come problema di min:
	- $max(3x_{1}+7x_{2})\quad\overset{\text{risolvo}}{ \implies }\quad min(-3x_{1}-7x_{2}) \quad\implies\quad -min(3x_{1}-7x_{2})$
- Vincolo di $\leq$ si trasforma in vincolo di $=$ aggiungendo una variabile di SCARTO (SLACK) $+\ x_{n+1}$
	- $4x_{1}+5x_{2}\leq 12 \implies 4x_{1}+5x_{2}+\textcolor{red}{x_{3}}=12$
- Vincolo di $\geq$ si trasforma in vincolo di $=$ sottraendo una variabile di SURPLUS $-x_{n+1}$
	- $4x_{1}+5x_{2}\geq 12 \implies 4x_{1}+5x_{2}\textcolor{red}{-x_{3}}=12$
- Variabile $x_{j}\leq 0$, Si moltiplica per -1 e si rinomina:
	- $x_{j}\leq 0 \implies -x_{j}\geq 0 \implies \hat{x}_{j}=-x_{j}$
	- $x_{j}$ si sostituisce in tutti i vincoli e nella f.o.
- Variabile $x_{j}$ libera in segno, si introducono due variabili $x_{j}'\ ;\ x_{j}''\geq 0$, e si pone $x_{j}=x'_{j}-x''_{j}$, e poi si sostituisce la variabile.

# Forma Standard e Vertici

Partendo da un esempio: