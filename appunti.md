---
title: "Appunti Elettronica generale"
author: [Leonardo Toccafondi]
date: 2024-04-12
subject: "Elettronica"
tags: [Appunti]
titlepage: true
chapters: true
chaptersDepth: 3
header-includes:
- |
  ```{=latex}
            \usepackage{cancel}
            \usepackage{tikz}
            \usepackage{circuitikz}
            \usepackage{steinmetz}
            \usepackage{derivative}
            \usepackage{tabularray}
            \usepackage{mathtools}
            \usepackage{siunitx}
            \usepackage{tcolorbox}
            \usepackage{geometry}
            \usepackage{array}
            \usepackage{caption}
            \usepackage{sectsty}
            \usepackage{hhline}
				\geometry{
					a4paper,
					total={170mm,257mm},
					left=20mm,
					top=20mm,
				}
            \tcbuselibrary{most}
            \newtcolorbox[auto counter,number within=section]{mybox}[1]{colback=red!5!white, colframe=red!75!black,fonttitle=\bfseries, title={#1}}
    ```
pandoc-latex-environment:
  tcolorbox: [box]

---

# Dispositivi elettronici

## Semiconduttori

I semiconduttori sono i materiali con cui sono composti i circuiti integrati.
Sono, come suggerisce il nome, materiali in cui il flusso di corrente *non è 
libero* (non è un conduttore), ma è **presente** (non è un'isolante).

In particolare, conducono in particolari situazioni. Quali sono però i
materiali con queste condizioni?

- Silicio (Si), Germanio (Ge) (Carbonio (C), ma composto)
- GaAs, GaN (Gallio-Arsenico/Azoto)
In generale sono gli elementi della $4°$ colonna della tavola periodica o
composti a numero medio di elettroni liberi pari a 4 (dai 3 ai 4).

\begin{mybox}{\emph{Silicio}}
Il silicio è il materiale semiconduttore \emph{"per eccellenza"} (da cui anche
il nome della famosa Silicon Valley), ma nella sua forma cristallina pura
ogni atomo forma un legame covalente\footnote{legame chimico in cui due atomi mettono
in comune delle coppie di elettroni.} con i suoi vicini "più prossimi":
per questo, a temperatura ambiente il silicio **non** è un gran conduttore
di elettricità.
\end{mybox}

Per dotare un materiale semiconduttore di conduttività *selettiva* è necessario
*"drogare"* il materiale stesso, ovvero aggiungere, in piccole dosi, nel reticolo
cristallino materiali della $5°$ colonna (drogaggio di tipo N), o elementi
della $3°$ colonna (tipo P). L'elemento drogante viene inserito
con un rapporto nell'ordine di $1:1^{10}$.

L'introduzione di un elemento drogante all'interno della struttura cristallina
di un semiconduttore comporta una modifica controllata delle sue proprietà
elettriche. L'atomo drogante, pur sostituendosi isomorficamente agli atomi del
reticolo ospite, presenta una valenza differente. Tale discrepanza induce la
formazione di livelli energetici aggiuntivi all'interno della banda proibita[^1]
del semiconduttore. In particolare, il drogaggio può essere di tipo P, qualora
l'elemento drogante presenti un elettrone di valenza in meno rispetto al
semiconduttore (es. boro nel silicio), oppure di tipo N, se l'elemento drogante
possiede un elettrone di valenza in più (es. fosforo nel silicio). Nel primo caso,
si genera un eccesso di lacune[^2], mentre nel secondo si ha un eccesso di elettroni liberi,
determinando così una variazione della conducibilità elettrica intrinseca del materiale.

La qualità del semiconduttore è influenzata dal materiale usato (per esempio Ge
è meglio del Si, ma è più raro), che è a sua volta influenzato dal goal[^3]
(elettronica digitale usa Si, l'elettronica di potenza il GaN o SiC).

Vediamo ora degli elementi in silicio.

[^1]:intervallo di energia interdetto agli elettroni
[^2]:assenza di elettroni
[^3]:(penso voglia dire "obiettivo perseguito")

### Giunzione P-N

Una giunzione P-N è formata da una sezione del semiconduttore drogata con un drogaggio P (con
una percentuale $N_{a}$, n. accettori) e un'altra sezione drogata con un drogaggio N (con una
percentuale $N_{d}$, n. donatori). \newline
Il materiale quindi è separato in due zone _nettamente distinte_, senza alterazione della
struttura cristallina all'interfaccia delle due zone. \newline
Il drogaggio è quantificato con le grandezze
$$
N_A = \frac{\# acceptors}{vol. unit} \text{ e } N_d=\frac{\# donors}{vol. unit}
$$
dove $N_a$ è tipo p:'positivo', mentre $N_d$ è di tipo n:'negativo'.

> Memo: il silicio puro ha una struttura cristallina matriciale, che blocca il passaggio di carica.

Collegando un blocco drogato tipo P ed uno tipo N abbiamo

[image1.1]: immagini/0.jpg "Giunzione P-N" 
![Giunzione P-N][image1.1]{width=30%}

L'abbondanza di lacune in p è considerabile come una carenza di elettroni, di cui n *abbonda*.
Ciò genera una **migrazione** di elettroni da N verso P, detta anche _corrente di diffusione_.

Tale fenomeno carica in modo *positivo* N (meno elettroni), e in modo *negativo* P (più elettroni).
\newline
Tali cariche generano dei campi elettrici (positivo su n e negativo su p), i quali impediscono un
ulteriore passaggio di carica, ottenendo allora un **equilibrio**.

> Inserire immagine

Nel punto di contatto si crea così una zona in cui tutte le lacune sono state riempite,
e tutti gli elettroni extra di p ceduti.
Tale zona è detta **depletion layer** (regione di svuotamento a carica spaziale), al cui
interno **non** vi sono portatori mobili.

[image1.2]: immagini/1.png "Regione di svuotamento"
![Regione di svuotamento][image1.2]{width=68%}

In genere la regione di svuotamento non è simmetrica: deve valere:
$$
x_P N_A = x_N N_D
$$

Come si vede nella figura seguente ($x_P$ e $x_N$ dipendono da $N_A$ e $N_D$).

* $N_A > N_D \to$ più è drogata la regione più la regione di svuotamento è piccola. 

Ricordando che $E=\int Q$, e che $V=\int E$, si vede come il potenziale **impedisca** il moto
$p\rightarrow n$ (delle lacune) e $n\rightarrow p$ (degli elettroni).

[image1.3]: immagini/2.png "Grafici relativi alla regione di svuotamento"
!["Grafici relativi alla regione di svuotamento"][image1.3]{height=35%}

Il simbolo circuitale della giunzione P-N, detta **diodo**[^4] è

\begin{center}
\begin{circuitikz}
  \draw (0,0) node[left]{A} to[diode,color=red] (2,0) node[right]{K};
\end{circuitikz}
\end{center}

[^4]: Un diodo è un dispositivo elettrico che permette alla corrente di muoversi attraverso
di esso in una direzione con molta più facilità che nell'altra.

dove a sinistra abbiamo un **anodo** A (dal greco *salita*), e a destra un **catodo** K 
(dal greco *discesa*).

#### Polarizzazione

In base all'applicazione di un potenziale sul diodo posso distinguere la:

* Polarizzazione **diretta** (forward bias): applico un potenziale positivo sull'anodo A e negativo sul catodo
K, "alzando" il potenziale

#### Diodi Speciali
\begin{center}
\begin{circuitikz}
  \draw (0,0) node[left]{+} to[diode, l_=Diodo normale] (2,0) node[right]{-};
  \draw (4,0) node[left]{-} to[diode, l_=Fotodiodo] node[right]{+} (6,0);
\end{circuitikz}
\end{center}
