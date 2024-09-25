---
title: "Appunti Elettronica generale"
author: [Leonardo Toccafondi]
date: 2024-04-12
subject: "Elettronica"
tags: [Appunti]
titlepage: true
chapters: true
chaptersDepth: 3
toc: yes
header-includes:
- |
  ```{=latex}
            \usepackage{cancel}
            \usepackage{tikz}
            \usepackage[version=4]{mhchem}
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
            \newtcolorbox[auto counter,number within=section]{mybox}[1]{colback=red!5!white, colframe=red!75!black,
            fonttitle=\bfseries, title={#1}}
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

- *Elementi semiconduttori*: Silicio (\ce{Si}), Germanio (\ce{Ge}) (Carbonio (\ce{C}), ma composto)
- *Elementi composti*: \ce{GaAs}, \ce{GaN} (Gallio-Arsenico/Azoto)
In generale sono gli elementi della $4°$ colonna della tavola periodica o
composti a numero medio di elettroni liberi pari a 4 (dai 3 ai 4).

\begin{mybox}{\emph{Silicio}}
Il silicio è il materiale semiconduttore sicuramente più diffuso. \newline
Un atomo presenta 4 elettroni (detti di \emph{valenza}) nello strato più esterno,
ma sua forma cristallina pura del silicio ogni atomo forma un legame covalente
\footnote{legame chimico in cui due atomi mettono in comune delle coppie di elettroni.}
con i suoi vicini "più prossimi".
Il cristallo di silicio puro ha inoltre una struttura cristallina matriciale,
che blocca il passaggio di carica. \newline
È da notare che all'aumentare della temperatura, qualche elettrone può rompere il legame
e muoversi liberamente nel cristallo.
\end{mybox}

Per dotare un materiale semiconduttore di conduttività *selettiva* è necessario
*"drogare"* il materiale stesso.
Il drogaggio, quindi, va a **modificare** la concentrazione di elettroni e di *lacune* [^1],
attraverso questo inserimento di impurità sostituzionali (ovvero atomi di elementi diversi,
i quali si sostituiscono ad alcuni degli atomi di silicio.) \newline
In pratica andiamo ad  aggiungere, in piccole dosi, nel reticolo cristallino materiali della
$5°$ colonna (drogaggio di tipo **n**, hanno 5 elettroni di valenza, sono detti donatori, ad esempio
il fosforo), o elementi della $3°$ colonna (tipo **p**, hanno 3 elettroni di valenza e sono detti 
**accettori**, ad esempio il boro).\newline
Tale discrepanza induce la formazione di livelli energetici aggiuntivi all'interno della banda 
proibita[^2] o "gap" del semiconduttore. Nel primo caso, si genera un eccesso di lacune,
mentre nel secondo si ha un eccesso di elettroni liberi, determinando così una variazione della conducibilità elettrica intrinseca del materiale. 

La qualità del semiconduttore è influenzata dal materiale usato (per esempio Ge
è meglio del \ce{Si}, ma è più raro), che è a sua volta influenzato dal goal[^3]
(elettronica digitale usa \ce{Si}, l'elettronica di potenza il \ce{GaN} o \ce{SiC}).

Vediamo ora degli elementi in silicio.

[^1]:assenza di elettroni dovuta alla **rottura** di un legame.
[^2]:intervallo di energia interdetto agli elettroni, distanza tra la banda di valenza di conduzione (nei semiconduttori distanti $1\si{eV}$)
[^3]:(penso voglia dire "obiettivo perseguito")

### Giunzione p-n

Una giunzione pn (o p-n) è formata da una sezione del semiconduttore drogata con un drogaggio p (con
una percentuale $N_{a}$, n. accettori) e un'altra sezione drogata con un drogaggio n (con una
percentuale $N_{d}$, n. donatori). \newline
Il materiale quindi è separato in due zone _nettamente distinte_, senza alterazione della
struttura cristallina all'interfaccia delle due zone. \newline
Il drogaggio è quantificato con le grandezze
$$
N_A = \frac{\# acceptors}{vol. unit} \text{ e } N_d=\frac{\# donors}{vol. unit}
$$
dove $N_a$ è tipo p:'positivo', mentre $N_d$ è di tipo n:'negativo'.

Collegando un blocco drogato tipo P ed uno tipo N abbiamo

[image1.1]: immagini/0.jpg "Giunzione P-N" 
![Giunzione P-N][image1.1]{width=30%}

Nella pratica parto da un blocco puro di silicio, per poi iniettare a *strati* il drogaggio.

L'abbondanza di lacune in p è considerabile come una carenza di elettroni, di cui n *abbonda*.
Ciò genera una **migrazione** di elettroni da N verso P, detta anche _corrente di diffusione_.

Tale fenomeno carica in modo *positivo* n (meno elettroni), e in modo *negativo* p (più elettroni).
\newline
Tali cariche generano dei campi elettrici (positivo su n e negativo su p), i quali impediscono un
ulteriore passaggio di carica, ottenendo allora un **equilibrio**.

Nel punto di contatto si crea così una zona in cui tutte le lacune sono state riempite,
e tutti gli elettroni extra di p ceduti.
Tale zona è detta **depletion layer** (regione di svuotamento a carica spaziale), al cui
interno **non** vi sono portatori mobili (di carica elettrica).

[image1.2]: immagini/1.png "Regione di svuotamento"
![Regione di svuotamento][image1.2]{width=68%}

In genere la regione di svuotamento non è simmetrica: deve valere:
$$
x_P N_A = x_N N_D
$$

Come si vede nella figura 1.3 ($x_P$ e $x_N$ dipendono da $N_A$ e $N_D$).

* $N_A > N_D \to$ più è drogata la regione più la regione di svuotamento è piccola. 

Ricordando che il campo elettrico $E=\int Q \,dq$, e che la tensione (o potenziale)
$V=\int E$, si vede come il potenziale **impedisca** il moto \colorbox{yellow}{(forse ulteriore?)}
$p\rightarrow n$ (delle lacune) e $n\rightarrow p$ (degli elettroni).

[image1.3]: immagini/2.png "Grafici relativi alla regione di svuotamento"
!["Grafici relativi alla regione di svuotamento"][image1.3]{height=35%}

### Diodo

Il simbolo circuitale della giunzione p-n, detta **diodo**[^4] è

\begin{center}
\begin{circuitikz}
  \draw (0,0) node[left]{A} to[diode,color=red] (2,0) node[right]{K};
\end{circuitikz}
\end{center}

[^4]: Un diodo è un dispositivo elettrico che permette alla corrente di muoversi attraverso
di esso in una direzione con molta più facilità che nell'altra. È il dispositivo più semplice che
fa uso di una giunzione p-n.

dove a sinistra abbiamo un **anodo** A (dal greco *salita*), e a destra un **catodo** K 
(dal greco *discesa*).

Sia la zone p che la zona n sono munite di un contatto elettrico (detto **reoforo**),
in modo tale che sia possibile applicarvi una tensione. È da notare come la zona n in
contatto col suo reoforo deve essere molto drogata \colorbox{yellow}{(approfondire)}.

#### Polarizzazione

In base all'applicazione di un potenziale sul diodo posso distinguere la:

* Polarizzazione **diretta** (forward bias): applico un potenziale positivo sull'anodo A e negativo
sul catodo K, "alzando" il potenziale

#### Diodi Speciali
\begin{center}
\begin{circuitikz}
  \draw (0,0) node[left]{+} to[diode, l_=Diodo normale] (2,0) node[right]{-};
  \draw (4,0) node[left]{-} to[diode, l_=Fotodiodo] node[right]{+} (6,0);
\end{circuitikz}
\end{center}

\appendix

# 

## Semiconduttori e bande

Gli elettroni in un solido allo stato fondamentale e a temperatura $0$ kelvin, in obbedienza alla
loro natura fermionica e al principio di Pauli che preclude ai fermioni il fatto di potersi
trovare in due nello stesso stato, riempiono gli stati elettronici loro consentiti partendo
dal livello energetico più basso via via su, fino a che tutti gli elettroni del solido hanno
trovato un'accomodazione. Si distribuiscono cioè rispettando la distribuzione di Fermi-Dirac
calcolata a temperatura 0 kelvin. Nei metalli, il livello energetico più alto occupato si 
definisce livello di Fermi.

![Schema semplificato della struttura elettronica a bande per metalli, semiconduttori e isolanti.](immagini/bande.png){width=50%}

A questo punto possono verificarsi diverse possibilità:

* Vi è una banda, o più di una fra le ultime riempite da elettroni, che è parzialmente riempita
e restano degli stati vuoti. In tal caso si ha a che fare con un metallo, cioè un sistema in cui
gli ultimi elettroni hanno la possibilità di spostarsi in livelli energetici molto vicini,
infinitesimalmente più alti in energia, e dunque hanno la possibilità di una mobilità elevata
che porta il sistema ad essere un buon conduttore di elettricità.
* L'ultima banda è stata riempita completamente in modo tale che il prossimo stato elettronico
consentito si trovi sulla banda successiva e fra questa banda e la banda completamente riempita
c'è una banda proibita (_band gap_) di energie. In tal caso il solido è un dielettrico.
* Si parla infine di semiconduttore nel caso di un isolante in cui la banda proibita è talmente
piccola che a temperatura ambiente c'è una certa probabilità che gli elettroni si trovino a
saltare la banda proibita per agitazione termica, e dunque il sistema si trovi in una situazione
prossima a quella di un metallo, con valori di conducibilità elettrica non nulli.

(N.B paragrafo proveniente da [Wikipedia][link1])

[link1]: https://it.wikipedia.org/wiki/Struttura_elettronica_a_bande 
