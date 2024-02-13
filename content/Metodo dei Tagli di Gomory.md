---
tags:
  - Ottimizzazione
  - Ottimizzazione/PLI
aliases:
  - Metodo di Gomory
---
![[Metodo dei piani di taglio#Schema Generale]]


# Metodo di Gomory

Genera il taglio sfruttando la tabella finale del [[Metodo del Simplesso|Simplesso]] del [[Problemi di Ottimizzazione Lineare Intera#Rilassamento Lineare|Rilassamento Lineare]] (RL).

In particolare, usa la riga della tabella associata ad una componente frazionaria della soluzione ottima del (RL).

Sia data la tabella finale della risoluzione del RL:

-- WIP

- $\beta_{r}$ è frazionario.
- $x^{OTT}_{RL}=(\beta_{1},\dots,\beta_{r},\dots,\beta m)$

$x^{OTT}_{RL}$ non è intero, supponiamo che $\beta_{r}$ non sia intero.

## Procedimento

Scriviamo la riga $r-$esima:

$\Large x_{r}+\alpha_{rm+1}x_{m+1}+\dots+\alpha_{rn}x_{n}=\beta_{r}$

e consideriamo i floor dei coefficienti:

$\Large x_{r}+\left\lfloor {\alpha_{rm+1}} \right\rfloor x_{m+1}+\dots+ \left\lfloor {\alpha_{rn}} \right\rfloor x_{n}= \left\lfloor {\beta_{r}} \right\rfloor$

Questo è il taglio di Gomory in forma intera.

Il taglio va aggiunto al rilassamento lineare dopo averlo reso standard. Si aggiunge il vincolo standard:


$\Large x_{r}+\left\lfloor {\alpha_{rm+1}} \right\rfloor x_{m+1}+\dots+ \left\lfloor {\alpha_{rn}} \right\rfloor x_{n}+x_{n+1}= \left\lfloor {\beta_{r}} \right\rfloor$

Come precedentemente detto, la convergenza è lenta. I primi tagli risultano più efficaci, ma lo sono meno continuando ad iterare l'algoritmo.

Se si opera un taglio alla volta e ci sono più valori frazionari si sceglie sempre la riga con indice minore, **oppure** quella con termine noto che ha la parte frazionaria maggiore.


> [!success]- Esempio (Grafico, lungo)
> EH, VOLEVI!
> wip.


