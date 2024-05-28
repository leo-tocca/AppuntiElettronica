---
title: "Appunti Elettronica generale"
#author: [Leonardo Toccafondi]
date: 2024-04-12
subject: "Elettronica"
tags: [Appunti]
titlepage: false
#mainfont: "Playfair-RegularSemiCondensed"
header-includes: |
            \usepackage{circuitikz}
            \usepackage{geometry}
				\geometry{
					a4paper,
					total={170mm,257mm},
					left=20mm,
					top=20mm,
				}
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

Collegando un blocco drogato tipo ? ed uno tipo ? abbiamo (ideale)

> Inserire immagine

L'abbondanza di lacune in $p$ è considerabile come una carenza di elettroni, di cui $n$ *abbonda*. Ciò genera una **migrazione** di elettroni da n verso p.

> Inserire immagine

Tale fenomeno carica in modo *positivo* n (meno elettroni), e in modo *negativo* p (più elettroni).

Tali cariche generano dei campi elettrici (positivo su n e negativo su p), che impedisce un ulteriore passaggio di carica, si ha allora un **equilibrio**.

> Inserire immagine

Nel punto di contatto si crea così una zona in cui tutte le lacune (di cosa?) sono state riempite, e tutti gli elettroni extra di ? ceduti.
Tale zona è detta **depletion layer** (regione di svuotamento a carica spaziale).

> Inserire immagine

In genere il dp non è simmetrico: deve valere:
$$
x_p N_A = x_n N_D
$$
Ricordando che $E=\int Q$, e che $V=\int E$, si vede come il potenziale **impedisca** il moto $p\rightarrow n$ (delle lacune) e $n\rightarrow p$ (degli elettroni).

Il simbolo circuitale della giunzione pn, detta **diodo** è
\begin{center}
\begin{circuitikz}
\draw (0,0) to[diode] (2,0); 
\end{circuitikz}
\end{center}
dove a sinistra abbiamo un **anodo** A (dal greco *salita*), e a destra un **catodo** (dal greco *discesa*).
