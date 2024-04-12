---
title: "Appunti Elettronica generale"
#author: [Leonardo Toccafondi]
date: 2024-04-12
subject: "Elettronica"
tags: [Appunti]
titlepage: false
#mainfont: "Playfair-RegularSemiCondensed"
...

# Semiconduttori

Sono, come suggerisce il nome, materiali in cui il flusso di corrente *non è libero* (non è un conduttore), ma è **presente** (non è un'isolante).

In particolare, conducono in particolari situazioni. Quali sono però i materiali con queste condizioni?
- Silicio (Si), Germanio (Ge) (Carbonio (C), ma composto)
- GaAs, GaN (Gallio-Arsenico/Azoto)
In generale sono gli elementi della $4°$ colonna della tavola periodica o composti a numero medio di elettroni liberi pari a 4.

Per far condurre un materiale va *"drogato"*, ossia aggiungere, in piccole dosi, materiali della $5°$ colonna (drogaggio di tipo N), che cedono *elettroni*,
o elementi della $3°$ colonna (tipo P), che acquistano elettroni.
La qualità del semiconduttore è influenzata dal materiale usato (per esempio Ge è meglio del Si, ma è più raro),
che è a sua volta influenzato dal goal[^1](elettronica digitale usa Si, l'elettronica di potenza il GaN o SiC).

Vediamo ora degli elementi in silicio.

[^1]:(penso voglia dire "obiettivo perseguito")

## Giunzione p-n
Il drogaggio di un  materiale è quantificato con le grandezze
$$
N_A = \frac{\# acceptors}{vol. unit} \text{ e } N_d=\frac{\# donors}{vol. unit}
$$
dove $N_a$ è tipo p:'positivo', mentre $N_d$ è di tipo n:'negativo'.

> Memo: il silicio puro ha una struttura cristallina matriciale, che blocca il passaggio di carica.
