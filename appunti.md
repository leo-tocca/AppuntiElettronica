---
title: "Appunti Elettronica Digitale"
author: [Leonardo Toccafondi]
date: 2024-04-12
subject: "Elettronica"
tags: [Appunti]
titlepage: true
link-citations: true
chapters: true
chaptersDepth: 3
toc: yes
header-includes:
- |
  ```{=latex}
            \usepackage{cancel}
            \usepackage{comment}
            \usepackage{float}
            \usepackage{multirow}
            \usepackage{subcaption}
            \usepackage{svg}
            \usepackage{tikz}
            \usetikzlibrary{patterns}
            \usepackage[version=4]{mhchem}
            \usepackage{circuitikz}
            \usepackage{pgfplots}
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
            \newtcolorbox[auto counter,number within=section]{redbox}[1]{colback=red!5!white, colframe=red!75!black,
            fonttitle=\bfseries, title={#1}}
            \newtcolorbox[auto counter,number within=section]{greenbox}[1]{colback=green!5!white, colframe=green!75!black,
            fonttitle=\bfseries, title={#1}}
            \newtcolorbox[auto counter,number within=section]{bluebox}[1]{colback=blue!5!white, colframe=blue!75!black,
            fonttitle=\bfseries, title={#1}}
    ```
pandoc-latex-environment:
  tcolorbox: [box]

---

# Dispositivi elettronici

## Semiconduttori

I semiconduttori sono i materiali con cui sono composti i circuiti integrati.
Sono, come suggerisce il nome, materiali in cui il flusso di corrente *non è 
libero* (non è un conduttore), ma è **presente** (non è un'isolante).\newline
In particolare, conducono in particolari situazioni. Quali sono però i
materiali con queste condizioni?

- *Elementi semiconduttori*: Silicio (\ce{Si}), Germanio (\ce{Ge}) (Carbonio (\ce{C}), ma composto)
- *Elementi composti*: \ce{GaAs}, \ce{GaN} (Gallio-Arsenico/Azoto)
In generale sono gli elementi della $14\textdegree$ colonna della tavola periodica o
composti a numero medio di elettroni liberi pari a 4 (dai 3 ai 4).

\begin{redbox}{\emph{Silicio}}
Il silicio è il materiale semiconduttore sicuramente più diffuso. \newline
Un atomo presenta 4 elettroni (detti di \emph{valenza}) nello strato più esterno,
ma sua forma cristallina pura del silicio ogni atomo forma un legame covalente\footnote{legame chimico in cui due atomi mettono in comune delle coppie di elettroni.}
con i suoi vicini "più prossimi".
Il cristallo di silicio puro ha inoltre una struttura cristallina matriciale,
che blocca il passaggio di carica. \newline
È da notare che all'aumentare della temperatura, qualche elettrone può rompere il legame
e muoversi liberamente nel cristallo.
\end{redbox}

Per dotare un materiale semiconduttore di conduttività *selettiva* è necessario
*"drogare"* il materiale stesso.
Il drogaggio, quindi, va a **modificare** la concentrazione di elettroni e di *lacune* [^1],
attraverso questo inserimento di impurità sostituzionali (ovvero atomi di elementi diversi,
i quali si sostituiscono ad alcuni degli atomi di silicio.) \newline
In pratica andiamo ad  aggiungere, in piccole dosi, nel reticolo cristallino materiali della
$5\textdegree$ colonna (drogaggio di tipo **n**, hanno 5 elettroni di valenza, sono detti **donatori**, ad esempio
il fosforo), o elementi della $3\textdegree$ colonna (tipo **p**, hanno 3 elettroni di valenza e sono detti 
**accettori**, ad esempio il boro).\newline
Tale discrepanza induce la formazione di livelli energetici aggiuntivi all'interno della banda 
proibita[^2] o "gap" del semiconduttore. Nel primo caso si genera un eccesso di lacune, le quali
si comportano come particelle cariche *positivamente*, mentre nel secondo si ha un eccesso di elettroni liberi, determinando così una variazione della conducibilità elettrica intrinseca del materiale. \newline
Non solo, sia le lacune che gli elettroni liberi sono quindi liberi di muoversi all'interno del
semiconduttore!\newline
La qualità del semiconduttore è influenzata dal materiale usato (per esempio Ge
è meglio del \ce{Si}, ma è più raro), che è a sua volta influenzato dal goal[^3]
(elettronica digitale usa \ce{Si}, l'elettronica di potenza il \ce{GaN} o \ce{SiC}).

Vediamo ora degli elementi in silicio.

### Giunzione p-n

Una giunzione pn (o p-n) si forma quando una del materiale semiconduttore intrinseco[^4] drogato con un drogaggio p (con
una percentuale $N_{A}$, n. accettori) viene posta a contatto con altro materiale semiconduttore drogato con un drogaggio n
(con una percentuale $N_{D}$, n. donatori). \newline
La concentrazione di ioni dalle seguenti "formule":
$$
N_A = \frac{\# acceptors}{vol. unit} \text{ e } N_D=\frac{\# donors}{vol. unit}
$$
dove $N_a$ indica il numero[^5] di ioni di tipo p:'positivo', mentre $N_d$ il numero di ioni di tipo n:'negativo'.

Collegando un blocco drogato tipo p ed uno tipo n abbiamo (idealmente)[^6]
\begin{figure}[H]
\centering
\begin{tikzpicture}[scale=1.5]
    \draw[very thick](-2,0)--(2,0)--(2,1)--(-2,1)--(-2,0);
    \draw[very thick](0,0)--(0,1);
    \draw[thick](0.5,0)--(0.5,1);
    \draw[thick](-0.5,0)--(-0.5,1);
    \node at (1.25,0.5) {$N$};
    \node at (-1.25,0.5) {$P$};
	 % Aggiungiamo le due righe orizzontali
    \draw[thick](-2.5,0.5)--(-2,0.5);
    \draw[thick](2,0.5)--(2.5,0.5);
    \draw[->](-0.25,0.5)--(0.25,0.5)node[above]{$V_0$};
\end{tikzpicture}
\caption{Giunzione pn}
\end{figure}

Il materiale quindi è separato in due zone _nettamente distinte_, senza alterazione della
struttura cristallina all'interfaccia delle due zone. \newline
L'abbondanza di lacune in p è, come sappiamo, corrispondente ad una carenza di elettroni, di cui n *abbonda*.
In altre parole questa diversa *densità* di portatori di carica genera una **migrazione** di elettroni da N verso P,
detta anche _diffusione[^7] (elettrica)_ $I_D$ oppure anche _corrente di diffusione_, che consiste quindi in

* lacune che si diffondono dalla regione (dal semiconduttore) drogata con p alla regione n;
* elettroni che si diffondono dalla regione drogata con n alla regione p.

> N.B.: Nella zona n i **portatori maggioritari** di carica sono le cariche negative, mentre nella zona p sono le cariche positive

Tale fenomeno carica in modo *positivo* il semiconduttore drogato n (meno elettroni), e in modo *negativo*
il semiconduttore drogato p (più elettroni). \newline
Le lacune che si diffondono dalla regione/zona p alla n si ricombinano con gli elettroni liberi, *scomparendo*. Di conseguenza, il numero di elettroni liberi nella zona n *diminuisce*, quindi non saranno più neutralizzate alcune cariche fisse positive (atomi donatori). Dal momento che questa ricombinazione avviene in prossimità della giunzione, accanto a questa si svilupperà una regione **svuotata** di elettroni, con cariche fisse positive non compensate. \newline
Analogamente nella zona p otterremo una zona svuotata dalle lacune e che comprende delle cariche fisse (in questo caso negative) non compensate.
 
\begin{figure}[H]
\centering
\begin{subfigure}[t]{0.6\textwidth}
\includegraphics[width=\textwidth,height=\textheight,keepaspectratio]{immagini/1.png}
\caption{Regione di svuotamento}
\end{subfigure}
\begin{subfigure}[t]{0.3\textwidth}
\includegraphics[width=\textwidth,height=\textheight,keepaspectratio]{immagini/pn_equilibrio.png}
\caption{Giunzione pn all'equilibrio}
\end{subfigure}
\end{figure}

Entrambe queste zone danno luogo alla **regione di svuotamento**[^8] (o di carica spaziale, in inglese *depletion layer*).
Inoltre lo spostamento delle cariche crea a cavallo della giunzione un campo elettrico, con la zona n positiva rispetto alla zona p. La presenza del campo elettrico comporta la presenza di una differenza di potenziale.
Questa è anche detta **barriera di potenziale**[^9], in quanto si oppone ad un'ulterore diffusione ai portatori di carica soggetti alla spinta della diffusione (si oppone al movimento di elettroni nella regione p e lacune nella regione n).
Una volta che la corrente di diffusione equivale la corrente di trascinamento[^10] $I_S$ raggiungiamo un **equilibrio** (dinamico):
la presenza del campo elettrico comporta la presenza di una differenza di potenziale.\newline
In genere la regione di svuotamento non è simmetrica: la seguente equazione regola la larghezza della regione:
$$
x_p N_A = x_N N_D
$$
dove $x_p$ e $x_n$ sono rispettivamente le **larghezze** della regione di svuotamento entro
il semiconduttore drogato p e drogato n.

\begin{figure}[H]
\includegraphics[height=0.5\textwidth, width=!]{immagini/2.png}
\centering
\caption{Grafici relativi al potenziale, al campo elettrico e alla carica nella giunzione pn}
\label{fig:1.3}
\end{figure}

Come si vede nella @fig:1.3 :

* $N_A > N_D \to$ più è drogata la regione più la regione di svuotamento è piccola. 

## I diodi

Il simbolo circuitale della giunzione p-n, detta **diodo**[^11] è

\begin{figure}[h]
\begin{centering}
\begin{circuitikz}
  \draw (0,0) node[left]{A} to[diode,color=red] (2,0) node[right]{K};
\end{circuitikz}
\caption{Diodo}
\end{centering}
\end{figure}

dove a sinistra abbiamo un **anodo** A (dal greco *salita*), e a destra un **catodo** K 
(dal greco *discesa*).\newline
Sia la zone p che la zona n sono munite di un contatto elettrico (detto **reoforo**),
in modo tale che sia possibile applicarvi una tensione.

### Polarizzazione

L'applicazione di un potenziale sul diodo viene detta **polarizzazione**, e si distingue la:

* Polarizzazione **diretta** (forward bias): applico un potenziale positivo sull'anodo A (lato p) e negativo
sul catodo K (lato n). La differenza di potenziale applicata ha la polarità *concorde* con la barriera di potenziale.
    - L'aumento della tensione determina una riduzione della barriera di potenziale, e di conseguenza della larghezza della
    regione di svuotamento. In questo modo aumenta il numero di elettroni e di lacune capaci di attraversare la giunzione
    tramite la diffusione.
    - La corrente di diffusione, rispetto a quella di deriva, aumenta rapidamente di svariati ordini di grandezza.
\begin{figure}[h]
\begin{centering}
\begin{circuitikz}
  \draw (0,0) node[left]{+} to[diode,color=blue] (2,0) node[right]{-};
\end{circuitikz}
\caption{Diodo polarizzato direttamente}
\end{centering}
\end{figure}
* Polarizzazione **indiretta** (reverse bias): applico un potenziale negativo sull'anodo e positivo sul catodo. In questo
caso la polarità della tensione applicata è discorde rispetto a quella della barriera di potenziale.
    - La regione di svuotamento si allarga, e la tensione di polarizzazione richiama le lacune verso il terminale negativo
    e gli elettroni verso il terminale positivo. Quindi l'ampiezza della barriera di potenziale aumenta.
    - La corrente di diffusione diminuisce fino ad annullarsi, mentre quella di deriva rimane (anche se è molto piccola e
    varia con la temperatura). Quindi quasi nessuna corrente riesce a scorrere.
    - Il campo elettrico incrementa fino ad ottenere il *breakdown*.

\begin{figure}[h]
\begin{centering}
\begin{circuitikz}
  \draw[thick] (0,0) node[left]{-} to[diode,color=orange] (2,0) node[right]{+};
\end{circuitikz}
\caption{Diodo polarizzato indirettamente}
\end{centering}
\end{figure}

### Equazione caratteristica e breakdown

In generale, la giunzione pn ha un'equazione caratteristica
$$
i=I_{S}(e^{\frac{V_d}{nV_t}}-1)
$$
detta **equazione di Shockley**:

* $V_d$ indica la differenza di potenziale applicati ai capi del diodo;
* $nV_t$ è il potenziale nativo dei diodi (pari a $\SI{0.7}{\volt}$), o *tensione termica*, pari a $\SI{26}{\mV}$.
* $I_S$ (o $I_0$) è una costante detta *corrente di saturazione* (per il \ce{Si} ha valori tra $10^{-15}$ e $10^{-19} \, \si{\ampere}$)

In condizioni di polarizzazione diretta la corrente è trascurabile per tensioni al di sotto di $0,5 - 0,6 \si{\volt}$ 
(per diodi al silicio) e dopo aver superato la *tensione di soglia* cresce molto repentinamente[^12]. \newline
Quando il diodo è in polarizzazione inversa, aumentando la tensione la corrente rimane costante finché
non si raggiunge la cosiddetta **tensione di breakdown** (o di rottura). Una volta oltrepassata la corrente
aumenta \colorbox{yellow}{(forse in questo caso \textit{diminuisce})} in maniera drastica a tensione praticamente costante.
\begin{greenbox}{Il \emph{breakdown}}
Il fenomeno del breakdown è dovuto a:
\begin{enumerate}
\item Effetto \emph{Zener}: prevalente per tensioni di breakdown inferiori alla decina di volt. Quando il diodo è polarizzato
    inversamente e la tensione è compresa tra $0\si{\volt}$ e $V_Z$ (inferiore a zero), si comporta quasi come un circuito aperto,
    seppur continui a scorrere una piccola corrente di saturazione inversa, oltre $V_Z$ la banda di valenza della regione p si
    avvicina talmente tanto alla banda di conduzione che alcuni elettroni si spostano dall'una all'altra;
\item Effetto \emph{valanga} (avalanche): prevalente per tensioni di breakdown superiori alla decina di volt. Si manifesta
    in presenza di campi elettrici \emph{molto elevati}, dovuti alla presenza di una tensione "moderata", ma imposta su distanze
    molto corte.
\end{enumerate}

Solitamente il processo del breakdown è irreversibile, tranne per i diodi Zener, i quali sono ideati per andare in breakdown.
\end{greenbox}
\begin{figure}[H]
    \centering
    \includegraphics[width=0.5\textwidth]{immagini/iv_pn.png} % replace with your image file
    \caption{Una tipica caratteristica I-V di un diodo a giunzione PN}
    \label{fig:caratteristica_pn}
\end{figure}

### Diodi Speciali

#### Fotodiodi

I fotodiodi sono diodi in cui la giunzione è "scoperta", o incapsulata in un materiale trasparente, 
in quanto vogliamo che sia in grado di **emettere** una corrente elettrica sfruttando l'effetto fotoelettrico.
Difatti è un *trasduttore*[^13] da un segnale ottico ad un elettrico.
\newline
L'equazione caratteristica del fotodiodo è pari a quella di un diodo normale, con l'aggiunta di un termine
$I_{ph}$, che rappresenta la corrente *fotogenerata*[^14]:
$$
i=I_{S}(e^{\frac{V_d}{nV_t}}-1)-I_{ph}
$$

\begin{center}
\begin{circuitikz}
  \draw (0,0) node[left]{+} to[diode, l_=Diodo normale] (2,0) node[right]{-};
  \draw[pD={}, l_=Fotodiodo] (4,0) node[left]{+} to node[right]{-} (6,0);
\end{circuitikz}
\end{center}


I fotodiodi p-n possono essere utilizzati senza essere polarizzati: sono adatti per "applicazioni" in situazioni
di bassa luminosità. Quando sono illuminati, il campo elettrico nella regione di deplezione aumenta, 
producendo la corrente fotogenerata la quale è cresce all'aumentare del flusso di fotoni. \newline
Altrimenti i fotodiodi operano in *polarizzazione inversa*, in modo tale che i fotoni (del colore "giusto")
possedano energia sufficiente ad oltrepassare la barriera di potenziale e a condurre quindi corrente
elettrica.

#### Led

I **led** (*light emitting diode*) è un tipo di diodo che **converte** energia elettrica in luce.
Sono formati da sottili strati di materiali semiconduttori fortemente drogati, i quali 
caratterizzano i diversi colori emessi quando viene applicata una polarizzazione *diretta*.\newline
Da un punto di vista *costruttivo* i led sono ricoperti da uno strato spesso di resina[^15] **trasparente**
di forma emisferica, sia per proteggere il led stesso sia per convogliare la luce emessa.

\begin{figure}[h]
\centering
\begin{circuitikz}[american]
\draw[pD={}](0.5,-0.5)to(2.0,-0.5);
\end{circuitikz}
\caption{Simbolo circuitale di un led}
\end{figure}

Applicando quindi una tensione positiva all'anodo, riduciamo la barriera di potenziale, in modo
tale che elettroni e lacune ricombinandosi generino fotoni pari al gap tra la banda di conduzione
e quella di valenza.

Come si può vedere nella tabella sottostante, al fine di generare un colore visibile, deve essere
fornita una tensione almeno pari a $1,5 \si{\volt}$

\begin{table}[H]
    \centering
    \begin{tabular}{|c|c|c|c|}
    \hline
        \textbf{Semiconduttore composto} & \textbf{$V_{F}$ a $20$ mA} & \textbf{Banda di lunghezza d'onda} & \textbf{Colore} \\ \hline
        GaInN & 4.0V & 450 nm & Bianco \\ \hline
        SiC & 3.6V & 430-505 nm & Blu \\ \hline
        GaAsP & 22V & 585-595 mm & Giallo \\ \hline
        GaAsP & 2.0V & 605-620nm & Ambra \\ \hline
        GaAsP & 1.8V & 630-660nm & Rosso \\ \hline
        GaAs & 1.2V & 850-940nm & Infrarosso \\ \hline
    \end{tabular}
    \caption{Diverse tipologie di led in base al colore prodotto}
\end{table}

#### Diodo Schottky

In questa tipologia di diodo la giunzione p-n è data dall'unione del metallo (che svolge il ruolo della regione
p) con un materiale semiconduttore drogato n. In questo modo si viene a creare una *"barriera Schottky"*: questa,
a differenza della giunzione p-n standard, ha una *bassa* tensione di giunzione (o tensione di soglia).
Infatti ai capi di un diodo Schottky si misura solitamente una differenza di potenziale tra i $0.15\si{\volt}$ e i
$0,45 \si{\volt}$: così facendo abbiamo una maggior efficienza e una maggior velocità di commutazione, riducendo i tempi
di turnoff[^16]! \newline
Inoltre, nella zona della giunzione del metallo, la zona di svuotamento è **nulla o quasi inesistente**[^17].


\begin{figure}[h]
\centering
\begin{circuitikz}[american]
\draw[sD={}](0.5,-0.5)to(3.0,-0.5);
\end{circuitikz}
\caption{Simbolo circuitale di un diodo Schottky}
\end{figure}

#### Diodo Zener

Questa tipologia di diodo lavora in **breakdown**. Se viene applicata una polarizzazione *diretta*
esso lavora e funziona come un diodo "qualsiasi". Invece, se viene applicata una polarizzazione *inversa*
la tensione di breakdown è "molto precisa": in questo modo se $V_G < V_Z$ non accade nulla $(V_G = V_Z)$,
mentre se $V_G \geq V_Z$ allora il diodo va in breakdown e su esso scorre una corrente. Ho quindi
una tensione di uscita *stabilizzata* $(V_O = V_Z)$.\newline
Nel circuito della figura seguente la resistenza è molto importante, in quanto se non fosse presnete
$i_R = \frac{V_G - V_i}{R}$, ma $R\to0$ e quindi $i_{R}\to \infty$

\begin{figure}[H]
\centering
\resizebox{0.25\textwidth}{!}{%
\begin{circuitikz}
\tikzstyle{every node}=[font=\normalsize]
\draw (0,2.25) to[american voltage source, invert] (0,0.25);
\draw (0,2.25) to[R] (3,2.25);
\draw[zzD={}](3,0.25) to(3,2.25);
\draw (0,0.25) to[short] (3,0.25);
\draw (2.75,2.25) to[short, -o] (4,2.25);
\draw (3,0.25) to (3,0) node[ground]{};
\draw [->, >=Stealth] (1,1.75) -- (2,1.75);
\node [font=\normalsize] at (1.5,1.5) {$i_{R}$};
\node [font=\normalsize] at (0.75,0.75) {$V_{G}$};
\node [font=\normalsize] at (4.5,2.25) {$V_{o}$};
\end{circuitikz}
}%

\label{fig:my_label}
\caption{Schema di un diodo Zener}
\end{figure}

# I transistor

## Introduzione

Un transistor è un dispositivo a semiconduttori utilizzato per interrompere (commutare) o amplificare 
segnali elettrici, come se fosse una **valvola**[^18]: in pratica regola la corrente che scorre
in una maglia (quella in uscita al circuito) tramite la tensione applicata ad un'altra
(ovvero quella in ingresso al circuito). \newline
Quando viene utilizzato come interruttore, un transistor è un dispositivo logico a *due stati*:
ON e OFF (binario 1 e 0). Sulla base di questo vengono realizzate *porte logiche* più complesse,
quali AND, OR, NOT, le quali a loro volta sono impiegate per realizzare tutti quei dispositivi
che compongono la parte **digitale** dell'elettronica (famiglie logiche, memorie etc.). \newline
Invece, quando viene utilizzato come modulatore di corrente, un transistor è a "semplicemente"
un **amplificatore**[^19].

## Bipolar Junction Transistor: i BJT

A differenza dei diodi a giunzione, i *transistor bipolari* utilizzano tre strati di materiali
semiconduttori, in pratica otteniamo due diodi posti in *antiserie*[^20], in modo tale da 
"condividere" uno strato.[^21] \newline
Ad ogni strato sarà associato un *terminale[^22]*: quello che sarà detto **base**, che a sua volta
separa due terminali drogati con gli stessi materiali (opposti al materiale della base), che saranno detti rispettivamente
**collettore** ed **emettitore**. \newline
I dispositivi BJT sono dispositivi *bipolari* in quanto il processo di conduzione coinvolge
portatori di *entrambe le polarità*.
\newline
La struttura di un transistor BJT può essere realizzata in due modi: quello **npn** e quello **pnp**.
È importante notare come in un transistor la zona dell'emettitore è significativamente più 
drogata di quelle di base e di collettore; si indica infatti con p+ nei transistori pnp e con n+ nei transistori npn.

\begin{figure}[H]
\centering
    \begin{subfigure}[b]{0.45\textwidth}
    \centering
    \begin{circuitikz}
        \draw (0,0) node[npn](Q){};
        \draw[thick] (-0.25,0) circle(0.5);
        \draw (-1.5,0)node[left]{$B$}to[short,i=$I_B$,*-](Q.B);
        \draw (0,1.5)node[above]{$C$}to[short,i_=$I_C$,*-](Q.C);
        \draw (Q.E)to[short,i_=$I_E$,-*](0,-1.5)node[below]{$E$};
        
        \draw[->](0.25,-1.375)to[out=45,in=315](0.25,1.375);
        \draw[->](-0.25,-1.5)to[out=180,in=270](-1.5,-0.25);
        \draw[->](-0.25,1.5)to[out=180,in=90](-1.5,0.25);
        \node at (1.3,0){$V_{CE}$};
        \node at (-1.375,-1.375){$V_{BE}$};
        \node at (-1.375,1.375){$V_{CB}$};

    \end{circuitikz}
    \caption{Transistor npn}
    \end{subfigure}
    \begin{subfigure}[b]{0.45\textwidth}
    \centering
    \begin{circuitikz}
        \draw (0,0) node[pnp](Q){};
        \draw[thick] (-0.25,0) circle(0.5);
        \draw (-1.5,0)node[left]{$B$}to[short,i<=$I_B$,*-](Q.B);
        \draw (0,-1.5)node[below]{$C$}to[short,i<=$I_C$,*-](Q.C);
        \draw (Q.E)to[short,i<=$I_E$,-*](0,1.5)node[above]{$E$};
        
        \draw[->](0.25,-1.375)to[out=45,in=315](0.25,1.375);    
        \draw[<-](-0.25,1.5)to[out=180,in=90](-1.5,0.25);
        \draw[<-](-0.25,-1.5)to[out=180,in=270](-1.5,-0.25); %VBC
        \node at (1.3,0){$V_{EC}$};
        \node at (-1.375,1.375){$V_{EB}$};
	    \node at (-1.375,-1.375){$V_{CB}$};
    \end{circuitikz}
    \caption{Transistor pnp}
    \end{subfigure}
    \caption{Transistor BJT}
\end{figure}

\begin{figure}[H]
    \centering
    \begin{subfigure}[b]{0.45\textwidth}
        \centering
        \includegraphics[width=\textwidth]{immagini/npn.png}
        \caption{Caption for image 1}
        \label{fig:image1}
    \end{subfigure}
    \hfill
    \begin{subfigure}[b]{0.45\textwidth}
        \centering
        \includegraphics[width=0.75\textwidth]{immagini/pnp.png}
        \caption{Caption for image 2}
        \label{fig:image2}
    \end{subfigure}
    \caption{Overall caption for the figure}
    \label{fig:subfigures}
\end{figure}


Come è possibile notare dalle figure precedenti, da un punto di vista circuitale i transistor BJT sono rappresentati
utilizzando 3 terminali: $\to$ nel simbolo indica la giunzione (e ne è riportata solo una), mentre
le frecce indicano i versi delle tensioni (dove sono maggiori). Parlando del transistor npn, 
per quanto riguarda le correnti abbiamo che all'equilibrio $I_B + I_C = I_E$, ed $I_B, I_C$ sono
entranti, mentre $I_E$ è uscente.

Per entrambe le tipologie di BJT, da un punto di vista costruttivo valgono queste regole:

1. La regione dell'emettitore è altamente drogata e ha il compito di emettere o iniettare portatori di corrente nella regione di base. Nei transistor npn, l'emettitore di tipo n immette elettroni liberi nella base, mentre nei transistor pnp, l'emettitore di tipo p introduce lacune nella base.
2. La base è sottile e leggermente drogata. La maggior parte dei portatori di corrente iniettati nella regione di base si muove verso il collettore senza fuoriuscire dal conduttore della base.
3. La regione del collettore è moderatamente drogata ed è la più grande all'interno del transistor. La sua funzione consiste nel raccogliere o attrarre i portatori di corrente iniettati nella regione di base.


## Bipolar Junction Transistor: i BJT

Il transistor BJT è stato il primo transistor ad essere prodotto su larga scala, precedendo di una decade l'introduzione dei transistor ad **effetto di campo**.

I BJT sono un dispositivo a semiconduttore a **tre** terminali, realizzato tramite due giunzioni p-n. Sono **bipolari** in quanto il processo di conduzione coinvolge portatori di _entrambe le polarità_: quindi sia lacune che elettroni. \newline
La realizzazione fisica consiste nell'utilizzo di tre strati di materiale semiconduttore, collegati ognuno ad un proprio terminale: abbiamo due strati esterni composti con lo stesso materiale drogante (**collettore** ed **emettitore**), ed un secondo strato posto tra gli altri due all'interno del quale viene introdotto un materiale drogante opposto (**base**). Così facendo otteniamo due giunzioni p-n: una base-emettitore ed una base-collettore.

\begin{redbox}{\emph{Configurazione a diodi}}
In generale un transistor BJT è \textbf{quasi equivalente }a porre due diodi in antiserie\footnote{Antiserie indica, per bipoli polarizzati, una connessione in serie (quindi un solo punto di contatto), in cui le polarità dei terminali vengono accoppiate per segni uguali}. In realtà è più vicina una configurazione di due giunzioni p-n poste l'una di seguito all'altra e orientate in senso inverso (ognuna delle quali con la propria regione di svuotamento). Questo perché per \emph{far funzionare} il transistor BJT è necessaria la presenza di un'\emph{unica} regione di base, che svolge un ruolo cruciale nel controllo della corrente. Quando si affiancano due diodi, l'interazione tra le loro giunzioni non riproduce le caratteristiche di amplificazione e controllo della corrente tipiche di un BJT, in quanto l'introduzione di un metallo nel circuito non permette la corretta gestione delle correnti e delle tensioni necessarie per il funzionamento del transistor: non vi è il campo elettrico necessario a far passare gli elettroni da un diodo all'altro passando per il filo metallico.
\end{redbox}

È possibile realizzare la struttura in due diverse modalità:

- tipo **npn**
- tipo **pnp**

I transistor npn sono usati più frequentemente. Inoltre le regole ed i risultati ottenuti possono essere estesi ai transistor pnp modificando opportunamente i versi di tensioni e correnti.

### Il BJT npn

Un BJT npn è formato da due sezioni di tipo n (emettitore e collettore), e da una di tipo p. 
Di fondamentale importanza per la fabbricazione di un BJT è lo _spessore della base_. Infatti deve essere il più **sottile** possibile, senza fare un corto circuito tra le regioni del collettore e dell emettitore.

In base alle polarizzazioni applicate alle giunzioni base-collettore e base-emettitore, otteniamo 4 **regioni di funzionamento** del transistor BJT:

\begin{table}[h]
\centering
\begin{tabular}{|c|c|c|}
\hline
\multicolumn{2}{|c|}{\textbf{Polarizzazione delle giunzioni}} & \multirow{2}{*}{\textbf{Regione di funzionamento}} \\ \cline{1-2}
\emph{B-E} & \emph{B-C} &  \\ \hline
Inversa & Inversa & Cutoff (Spento) \\ \hline
Diretta & Inversa & Attiva Diretta \\ \hline
Diretta & Diretta & Saturazione \\ \hline
Inversa & Diretta & Attiva Inversa \\ \hline
\end{tabular}
\caption{Regioni di funzionamento in base alla polarizzazione delle giunzioni}
\label{tab:reg-bjt}
\end{table}

#### Regioni di funzionamento

##### Cutoff

In questa regione il transistor è *spento*. Entrambe le giunzioni sono polarizzate inversamente: le rispettive tensioni sono ambedue **sotto soglia**. In particolare $V_{BE}<V_{\text{soglia}}$ e $V_{BC}<0$. \newline
Dato che la giunzione BE non è polarizzata $\to i_B = 0$.
Inoltre, dato che tutte le giunzioni sono polarizzate inversamente, anche la corrente del collettore è *nulla*.
 $\to i_C = 0$ \newline
Nel grafico, la corrente non è esattamente nulla dato che secondo la legge di $I_D$ in una giunzione con polarizzazione inversa la corrente vale $I_O$.

> In definitiva non vi è conduzione.

##### Attiva diretta

In questa regione la giunzione BE è polarizzata *direttamente*, mentre la giunzione BC è polarizzata inversamente. Significa che:

- $V_{BE} > V_{\text{soglia}}$
- $V_{BC} < 0$

La corrente $I_B >0$, e nonostante la tensione della giunzione BC sia negativa, $I_C= h_{fe}I_{b}$. \newline
Dunque gli elettroni dovrebbero ricombinarsi e "richiudersi" verso la base. Tuttavia, sapendo che la base è "corta" gli elettroni raggiungono il collettore prima di ricombinarsi, il quale li prende (forse meglio dire li accetta), in quanto possiede un potenziale *positivo*. È da notare che comunque non tutti gli elettroni riescono ad attraversare tutto il transistor, statisticamente alcuni si ricombinano con le lacune presenti nella regione della base.

Il [^23]**guadagno[^24] del transistor di corrente** è $h_{fe}=\frac{I_C}{I_B}$. Il transistor ha una funzione di *amplificatore* della corrente di base nel caso in cui $h_{fe}$ sia un valore alto: ciò lo rende **_"attivo"_**

> In questa regione funge da generatore di corrente controllato in corrente.

##### Saturazione

In questa regione anche la giunzione BE è polarizzata direttamente:

- $V_{BE}< V_{\text{soglia}}$
- $V_{CE}<V_{CE -sat}$

Se vale quest'ultima condizione (la tensione della giunzione BE è bassa) allora anche BC è polarizzata direttamente. Per lo stesso motivo gli elettroni non vengono "raccolti" dal collettore, tendendo a rimanere nella base: 

- $I_{B}>0$
- $I_C < h_{fe}\ I_{B}$

> È da notare come in questa configurazione/regione otteniamo una tensione in uscita **costante** $V_{CE - sat}$

##### Regione attiva inversa

In questo caso $V_{BE}<0$ e $V_{BC} > V_{\text{soglia}}$. Quindi gli elettroni si spostano nel collettore. In questo caso il *guadagno di corrente è $\leq 1$: $\ I_{e} \simeq - I_{B}$.

> Otteniamo un guadagno di corrente molto basso (tipicamente $\leq 1$)

![Curva BJT.](assets/imgs/curva_bjt_npn.png){width=70%}

In questo grafico sono rappresentate delle curve che riportano gli andamenti di $I_C$ in funzione di $V_{CE}$ con $I_B$.

### Layout planare di un transistor NPN

\begin{figure}[H]
\centering
\resizebox{0.25\textwidth}{!}{%
\begin{circuitikz}
\tikzstyle{every node}=[font=\large]
\draw [thick, fill=blue!20](0,4.25) rectangle (5,0.25);
\draw [thick, fill=red!20]  (1,4.25) rectangle (4,2.25);
\draw [thick, fill=blue!20] (2,4.25) rectangle (3,3.25);
\draw [short] (0,1.25) -- (5,1.25);
\draw [short] (2.5,0.25) -- (2.5,-0.25);
\draw [short] (2.5,4.75) -- (2.5,4.25);
\draw [short] (3.5,4.75) -- (3.5,4.25);
\node [font=\large] at (2.5,0.75) {n+};
\node [font=\large] at (2.5,1.75) {n};
\node [font=\large] at (2.5,2.75) {p};
\node [font=\large] at (2.5,3.75) {n+};
\node [font=\normalsize] at (2.5,5) {Emettitore};
\node [font=\normalsize] at (3.75,5) {Base};
\node [font=\large] at (2.5,-0.5) {Collettore};
\end{circuitikz}
}%
\centering
\caption{Configurazione planare di un BJT npn}
\label{fig:my_label}
\end{figure}

Come mostra anche lo schema, da un punto di vista fisico il layout planare di un transistor BJT npn *non è simmetrico*: questo sia per il drogaggio, sia per la realizzazione del dispositivo stesso. L'emettitore è molto piccolo e molto drogato, mentre le regioni della base e del collettore sono (viceversa) molto grandi e poco drogate. \newline
I contatti della base, dell'emettitore e del collettore sono *metallici* (se legati a zona n viene un diodo di silicio). Dato che i materiali $n^{+}$ sono molto drogati la regione di svuotamento è molto piccola e gli elettroni la possono attraversare come se non ci fosse.

### Il BJT pnp

È un dispositivo *complementare* al pnp: valfolo le stesse equazioni, ma tensioni e correnti sono **opposte** \newline
Sia le prestazioni che il guadagno sono **minori**, perché i portatori in movimento sono le *lacune*, più lente rispetto agli elettroni.

### Transistor "speciali"

#### Foto transistor

Il phototransistor è caratterizzato da una corrente di base *"photo-generated"*[^25]. Il resto dei parametri
di lavoro sono gli stessi un un normale BJT.
$$
I_C = k \cdot P_{L}
$$
dove $P_L$ è la potente luminosa.\newline
È importante che il dispositivo si trovi in regione attiva: per questo sarà inserito un resistore dal lato del collettore per evitare di andare in saturazione.

\begin{figure}[H]
\centering
\begin{circuitikz}[american]
\draw(1.0,-1.0) node[npn,photo,scale=0.59](Q1){};
\draw[short](Q1.C)to(1.0,-0.5);
\draw[short](Q1.E)to(1.0,-1.5);
\draw(2.0,-1.0) node[pnp,photo,scale=0.59](Q2){};
\draw[short](Q2.E)to(2.0,-0.5);
\draw[short](Q2.C)to(2.0,-1.5);
\end{circuitikz}
\caption{Un fototransistor npn ed uno pnp}
\end{figure}

\begin{figure}[H]
\centering
\resizebox{0.25\textwidth}{!}{%
\begin{circuitikz}
\tikzstyle{every node}=[font=\normalsize]
\draw (0,2) to[R] (0,0);
%\draw (0,0) to[npn, photo] (0,-2);
\draw(0.0, 0.0) node[npn,photo,scale=0.7](0,-3){};
%\draw[short={}](0.0,-2)to(-2.0,-3.0);
\node at (0,2) [circ] {};
\node [font=\normalsize] at (0.5,2) {$V_{CC}$};
\node [font=\normalsize] at (0.5,1) {$R$};
\node [font=\normalsize] at (2.25,0) {$V_{CE} = V_{CC} - R \cdot I > 0.2$};
\end{circuitikz}
}%

\label{fig:my_label}
\caption{Schema con fototransistor npn}
\end{figure}

## I transistor MOS

I **MOSFET** (*Metal Oxide Semiconductor Field Effect Transistor*) sono una tipologia di transistor appartenente ai transistor ad **effetto di campo**.

\begin{greenbox}{\emph{I transistor ad effetto di campo}}
I transistor ad effetto di campo sono caratterizzati dalla possibilità di controllare la \textbf{conduttività elettrica del dispositivo}, ovvero la quantità di corrente elettrica che attraversa il dispositivo stesso, attraverso la formazione di un \emph{campo elettrico}
all'interno di esso. \newline
Possono essere realizzati in diverse modalità: 
\begin{enumerate}
\item JFET: ovvero Junction-Fet, realizzato con una giunzione p-n come elettrodo "rettificante";
\item MESFET: abbreviazione di Metal Semiconductor FET realizzato tramite una giunzione Schottky raddrizzante metallo-semiconduttore; 
\item MOSFET: il più comune.
\end{enumerate}
\end{greenbox}

I MOS sono strutturati con più *strati di materiali sovrapposti*: metallo, ossido di silicio $(\ce{SiO_2})$ e del silicio, o di tipo $p$ o di tipo $n$. Si utilizza l'ossido come un *isolante*, non permettendo quindi il passaggio di cariche elettriche tra il metallo ed il semiconduttore.

Come per i transistor a giunzione, a seconda del drogaggio possiamo ottenere due tipologie diverse di transistor MOS: i nmos e i pmos. \newline
In particolare, sono dispositivi *controllati in tensione*.

### N-Mos

Nell'N-MOS (a canale $P$), il silicio è di tipo $n$: il drogaggio $n+$ favorisce il contatto ohmico[^26] con l'alluminio. Le definizioni delle correnti e delle tensioni equivalgono quelle dei transistor NPN.

\begin{figure}[H]
\centering
\resizebox{0.7\textwidth}{!}{%
\begin{circuitikz}
\tikzstyle{every node}=[font=\LARGE]

\draw[thick, fill=red!20]   (0,7.25) rectangle (11,3.25); %rettangolo principale
\draw[thick, fill=yellow!20]   (4,8.25) rectangle (7,7.25); %ossido
\draw[thick, fill=blue!20]   (2,7.25) rectangle (4,6.25); %n+
\draw[thick, fill=red!60]   (4,9.25) rectangle (7,8.25); %metal gate
\draw[thick, fill=blue!20]   (7,7.25) rectangle  node {\LARGE n+} (9,6.25);%n+
\node [font=\Large] at (5.5,5.25) {P};
\node [font=\Large] at (3,6.75) {n+};
\node [font=\Large] at (5.5,8.75) {Metal gate};
\node [font=\Large] at (5.5,7.75) {Ossido di S};
\node [font=\Large] at (3,8.5) {Source};
\draw [short] (3,8.25) -- (3,7.25);
\draw [short] (8,8.25) -- (8,7.25);
\node [font=\Large] at (8,8.5) {Gate};
\draw [short] (5.5,10.25) -- (5.5,9.25);
\node [font=\Large] at (5.5,10.5) {Drain};
\draw (20,8.5) to[Tnmos, transistors/scale=1.02] (20,4.5);
\draw  (20.25,6.5) circle (1cm);
\draw [<->, >=Stealth] (12,5.75) -- (16,5.75);
\draw [->, >=Stealth] (21.75,5.25) .. controls (22.5,6.5) and (22.25,7.25) .. (21.75,7.75)  node[midway, right] {$V_{CE}$};
\draw [->, >=Stealth] (20,8.5) -- (20,7.5);
\draw [->, >=Stealth] (21,6.5) -- (20.5,6.5);
\draw [->, >=Stealth] (18.5,6.25) -- (19.25,6.25);
\draw [short] (19.25,6.25) -- (19.75,6.25);
\draw [short] (19.75,6.75) -- (19.75,6.25);
\draw [->, >=Stealth] (20,5.5) -- (20,4.75);
\draw [short] (20,4.5) -- (21,4.5);
\node [font=\Large] at (17.75,6.25) {Gate};
\node [font=\Large] at (20,8.75) {Drain $\sim$ D};
\node [font=\Large] at (22.25,4.5) {Source $\sim$ S};
\node [font=\Large] at (20.5,7.75) {$I_D$};
\node [font=\Large] at (20,4) {$I_S$};
\draw [->, >=Stealth] (19.5,4.75) .. controls (18.75,5) and (18.75,5.25) .. (18.25,6)node[midway, right] {$V_{GS}$};
\draw [->, >=Stealth] (17.75,6) -- (17.75,5);
\node [font=\Large] at (17,4.5) {Terminale di controllo};

\node[font=\large, text=blue] at (5.5, 6.75) {- - Canale - -}; 
\end{circuitikz}
}%

\label{fig:my_label}
\caption{Sezione di un transistor N-MOS.}
\end{figure}

È da notare come solitamente il metallo utilizzato sia l'alluminio, anche se a volte può essere del silicio molto drogato. L'ossido, invece, è ossido di silicio.\newline
In generale qualsiasi MOSFET (quindi anche un N-MOS) ha tre terminali: ***source*** (emettitore), ***gate*** (base) e ***drain*** (collettore).

All'atto pratico si ha la corrente del gate sempre **nulla** (in regime continuo). L'ossido ha la funzione di isolante, inoltre la lastra (di metallo) è sottile $(\approx 10 nm)$, la quale *blocca* il passaggio di corrente dal gate al blocco sottostante, formando una struttura di un *condensatore a facce piane*.

Uno dei pregi dei transistor di tipo *MOS* è il **consumo**: un BJT ha un consumo di energia *costante* nel tempo (dal momento che deve mantenere la polarizzazione), mente un transistor MOS consuma solo durante le *transizioni*.

Come detto in precedenza la struttura di un transistor N-MOS è simile ad un condensatore, dove le piastre sono il gate, mentre la piastra sotto è l'ossido. Applicando una tensione positiva in GS (tra il gate e il source, $V_{GS}>0$), si accumulano sopra e sotto l'ossido delle cariche (che saranno positive *sopra* e negative *sotto*). Queste cariche andranno a riempire alcune lacune presenti sotto l'ossido, creando così un *depletion layer*.

Come in un condensatore, al crescere della tensione $V_{GS}$ aumenta anche l'accumulo delle cariche; superata una certa ***tensione di soglia*** $V_{T}$ $(V_{GS}>V_T)$, le cariche accumulate hanno riempito tutte le lacune, ed iniziano ad accumularsi sotto l'ossido: così facendo si va creare una regione caratterizzata da una **carica elettrica libera**, che collega S a G.

Come il BJT, anche con un transistor N-MOS si hanno diverse ***working regions***:

- ***Cutoff***: il dispositivo è **spento**, in quanto $V_{GS}<V_T$; si ha quindi corrente *nulla*, come un interruttore *aperto* $(i_D)=0$;
- ***Linear***: il dispositivo è in **conduzione** $V_{GS}>V_T$; non ha ancora raggiunto la massima corrente (di saturazione, $i_D<i_{D-sat}$). Esiste allora un *rapporto di proporzionalità* $i_D \propto V_{DS}$; il rapporto tra i due è detto ***resistenza di canale***.
- ***Saturation***: il dispositivo è **acceso** $V_{GS}>V_T$, ma ha *saturato*[^27] la corrente $(i_D=I_{sat})$. Questo è dovuto alla tensione di D; all'aumentare della tensione $V_{DS}$ con la tensione $V_GS$ fissata, oltre una certa soglia non otteniamo un aumento di corrente, dal momento che il drain D attira più elettroni di quanti ne inserisca S.
Indichiamo le caratteristiche di un Mos con due grafici:

![Curve caratteristiche di un transistor N-MOS.](assets/imgs/caratteristiche_NMOS.png){width=65%}

Come accennato prima abbiamo a che fare con un generatore di corrente *governato in tensione*, in particolare dalla $V_{DS}$, quella tra drain e source. L'*equazione della corrente è*:
$$
i_{D}= \left\{ \begin{array}{cl}
K[2(V_{GS}-V_{T})V_{DS}-V^{2}_{DS})] & : \ V_{DS} \leq V_{GS} - V_{T} \\
i_{D-sat}=k(V_{GS}-V_{T}) & : \ V_{DS} \geq V_{GS} - V_{T}
\end{array} \right.
$$
La prima equazione raffigura una *parabola* che ha come parametro la tensione $V_{DS}$: avrà il proprio vertice in $V_{GS}-V_{T}$.
$$
K=\frac{1}{2}\mu\:C_{ox}\frac{W}{L}
$$
Nel parametro $K,\:\mu$ dovrebbe essere la *mobilità*[^28] del materiale, $C_{ox}$ la capacità dell'ossido per unità di carica, mentre $W$ rappresenta la larghezza della zona che va a costituire il canale, mentre $L$ è la lunghezza.
$$
K\propto \mu \Rightarrow K_{n}\simeq 2K_{p}
$$
All'aumentare della corrente il N-MOS si comporta come un resistore la cui resistenza è data
da $R=\frac{\rho\cdot L}{s}$.

![Vista di un transistor N-MOS dall'alto.](assets/imgs/nmos_dall_alto.png){width=50%}

### P-MOS

È il dispositivo ***complementare all'N-MOS***.

\begin{figure}[H]
\centering
\resizebox{0.7\textwidth}{!}{%
\begin{circuitikz}
\tikzstyle{every node}=[font=\LARGE]

\draw[thick, fill=blue!20]   (0,7.25) rectangle (11,3.25); %rettangolo principale
\draw[thick, fill=yellow!20]   (4,8.25) rectangle (7,7.25); %ossido
\draw[thick, fill=red!20]   (2,7.25) rectangle (4,6.25); %n+
\draw[thick, fill=red!60]   (4,9.25) rectangle (7,8.25); %metal gate
\draw[thick, fill=red!20]   (7,7.25) rectangle  node {\LARGE p+} (9,6.25);%n+
\node [font=\Large] at (5.5,5.25) {N};
\node [font=\Large] at (3,6.75) {p+};
\node [font=\Large] at (5.5,8.75) {Metal gate};
\node [font=\Large] at (5.5,7.75) {Ossido di S};
\node [font=\Large] at (3,8.5) {Source};
\draw [short] (3,8.25) -- (3,7.25);
\draw [short] (8,8.25) -- (8,7.25);
\node [font=\Large] at (8,8.5) {Gate};
\node [font=\Large] at (5.5,10.5) {Drain};
\draw [short] (5.5,10.25) -- (5.5,9.25);
\draw [<->, >=Stealth] (12,5.75) -- (15,5.75);
\draw  (4,9.25) rectangle (7,8.25);
\draw (18.75,7.5) to[Tpmos, transistors/scale=1.5] (18.75,4.5);
\draw  (19.25,6) circle (1.1cm);
\draw [->, >=Stealth] (20.75,6.75) .. controls (20.5,7.5) and (20.5,7.75) .. (19.75,7.75) node[pos=0.5,right, fill=white]{$V_{SG}$};
\draw (19.75,6) to[short] (20.5,6);
\draw [->, >=Stealth] (17.5,4.75) .. controls (17,6) and (17,6) .. (17.5,7) node[pos=0.5,left, fill=white]{$V_{SD}$};
\node [font=\large] at (18.75,7.75) {$S$};
\node [font=\large] at (20.75,6) {$G$};
\node [font=\large] at (18.75,4.25) {$D$};
\draw [->, >=Stealth] (18.25,8) -- (18.25,7)node[pos=0.5,left, fill=white]{I};
\draw [->, >=Stealth] (20.5,5.5) -- (21.25,5.5)node[pos=0.5,below, fill=white]{I};
\end{circuitikz}
}%

\label{fig:my_label}
\caption{Sezione di un transistor P-MOS}
\end{figure}

Valgono le stesse equazioni, ma le tensioni e le correnti sono *opposte* ($V_{GS}<0,V_{DS}>0,V_{t}<0$).\newline
Applicando al Ground una tensione negativa si accumulano cariche positive *sotto l'ossido*: si formerà dunque un canale di lacune. Il guadagno (e quindi la corrente di uscita) sono *minori*, in quanto le lacune sono portatori minoritari (come per i transistor BJT, in quanto $k_n\approx 2k_p$).

Per valutare K dato delle curve è possibile risolvere il seguente sistema:
$$
\begin{cases}
I_{D1}=K(V_{G1}-V_{t})^{2}\\
I_{D2}=K(V_{G2}-V_{t})^{2}\end{cases}\longrightarrow\begin{cases}\sqrt{I_{D1}}=\sqrt{K}(V_{G1}-V_{t})\\
\sqrt{I_{D2}}=\sqrt{K}(V_{G2}-V_{t})
\end{cases}
$$

### Real N-MOS

All'apparenza il transistor N-MOS sembra un dispositivo *simmetrico*, ma non lo è. Infatti in precedenza abbiamo assunto la tensione $V_{DS}>0$ perché polarizzando la S viene polarizzato anche il blocco P[^29] sottostante: in questo modo si viene a formare un ***body diode*** tra l'emettitore ed il collettore.
\begin{redbox}{Body diode}
Il \textbf{body diode} sono diodi \textbf{\emph{intrinseci}} per qualsiasi transistor ad effetto di campo. Nelle applicazioni FET a canale N, la corrente scorre tipicamente dal drain alla source a causa della polarità del body diode. Anche se non è stato indotto un canale, la corrente può comunque fluire dalla source al drain attraverso la connessione in cortocircuito source-body e il diodo body-drain. Per questo motivo, un tipico FET a canale N non può bloccare il flusso di corrente dalla sorgente al drain.
\end{redbox}
Nel nostro caso è essenzialmente una giunzione p-n *parassita* in cui passa la corrente invece che nel canale.


\begin{figure}[h!]
  \centering
  \begin{minipage}{0.45\textwidth}
    \centering
    \resizebox{0.6\textwidth}{!}{ % Ridimensiona la figura al 80% della larghezza
      \begin{circuitikz}
        \tikzstyle{every node}=[font=\LARGE]
        \draw  (1,7.25) rectangle (10,3.25);
        \draw  (4,8.25) rectangle (7,7.25);
        \draw  (2,7.25) rectangle (4,6.25);
        \draw  (7,7.25) rectangle  node {\LARGE n+} (9,6.25);
        \node [font=\Large] at (5.5,5.25) {P};
        \node [font=\Large] at (3,6.75) {n+};
        \node [font=\Large] at (5.5,8.75) {Metal gate};
        \node [font=\Large] at (5.5,7.75) {Ossido di S};
        \node [font=\Large] at (3,8.5) {Source};
        \draw [short] (3,8.25) -- (3,7.25);
        \draw [short] (8,8.25) -- (8,7.25);
        \node [font=\Large] at (8,8.5) {Gate};
        \draw [short] (5.5,10.25) -- (5.5,9.25);
        \node [font=\Large] at (5.5,10.5) {Drain};
        \draw  (4,9.25) rectangle (7,8.25);
        \draw (5.5,3.25) to[D] (8,6.25);
      \end{circuitikz}
    }
    \caption{Presenza nel real N-MOS del body diode}
  \end{minipage}
  \hspace{1cm}
  \begin{minipage}{0.45\textwidth}
    \centering
    \begin{circuitikz}
      \draw (0,0) node[nigfete](M1){};
      \draw (M1.G) -- (-1,0) node[left]{Gate};
      \draw (M1.D) -- (0,1.2) node[above]{Drain};
      \draw (M1.S) -- (0,-1.2) node[below]{Source};
      \draw (1,-1) to[diode] (1,1);
      \draw (0,-1) to[short] (1,-1);
      \draw (0,1) to[short] (1,1);
    \end{circuitikz}
    \caption{Schema circuitale del real N-MOS}
  \end{minipage}
\end{figure}

Se $V_{DS}<0$ il diodo in questione è in *forward bias*, e la corrente $i_D$ non dipende più dal gate[^30]. Per evitarlo il drain dovrebbe essere positivo rispetto al source.

# Digital Logic Circuits (circuiti a logica digitale)

Servono per trasferire e processare informazioni, funzionano realizzando operazioni *booleane* su dati booleani.

## Operatori logici (booleani)

- **Not** (negazione)

\begin{figure}[h!]
  \centering
  \begin{minipage}{0.45\textwidth}
    \centering
    % Porta NOT con A e $\overline{A}$
    \begin{circuitikz}
      \node [not port](O1) at (0,0) {};    % Porta NOT
      \node at (-1, 0) {A};                 
      \node at (1, 0) {$\overline{A}$};     
    \end{circuitikz}
    \caption{Simbolo circuitale di NOT con A e $\overline{A}$}
  \end{minipage}%
  \hspace{0.5cm} % Spazio tra le due sottofigure
  \begin{minipage}{0.45\textwidth}
    \centering
    % Tabella di verità per NOT senza l'ambiente table
    \begin{tabular}{ll}
      A & $\overline{A}$ \\
      0 & 1              \\
      1 & 0             
    \end{tabular}
    \caption{Tabella di verità per NOT}
  \end{minipage}
\end{figure}

- **And**

\begin{figure}[h!]
  \centering
  \begin{minipage}{0.45\textwidth}
    \centering
    % Porta AND con A e B
    \begin{circuitikz}
      \node [and port](O1) at (0,0) {};    % Porta AND
      \node at (-2, 0.25) {A};                % A a sinistra
      \node at (-2, -0.3) {B};                 % B a destra
      \node at (0.75, 0) {A+B};                 % B a destra
    \end{circuitikz}
    \caption{Simbolo circuitale di AND con A e B}
  \end{minipage}%
  \hspace{0.5cm} % Spazio tra le due sottofigure
  \begin{minipage}{0.45\textwidth}
    \centering
    % Tabella di verità per AND
    \begin{tabular}{lll}
    A & B & A+B \\
    0 & 0 & 0   \\
    1 & 0 & 0   \\
    0 & 1 & 0   \\
    1 & 1 & 1  
    \end{tabular}
    \caption{Tabella di verità per AND}
  \end{minipage}
\end{figure}



# Esercizi

\begin{bluebox}{Le leggi di Kirchoff}
\begin{enumerate}
\item \emph{Legge di Kirchoff alle correnti}: la somma delle correnti in un nodo è pari a 0.
\item \emph{Legge di Kirchoff alle tensioni}: la somma delle tensioni lungo un percorso chiuso è pari a0.
\end{enumerate}
\end{bluebox}

## Esercizi capitolo 1

\begin{figure}[h]
\centering
\begin{circuitikz}[american]
\draw[V={}](2.0,-2.5)to(2.0,-5.5);
\draw[D={}](2.0,-2.5)to(6.5,-2.5);
\draw[R={}](6.5,-2.5)to(6.5,-5.5);
\draw[short={}](2.0,-5.5)to(6.5,-5.5);
\end{circuitikz}
\end{figure}


# Varie 

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

\begin{comment} 
TODO capire come funziona tavola periodica
## Tavola periodica

%%\pgfPT[show title=false, back color scheme=example,
%%  legend box={draw=blue!50,fill=blue!20},
%%  show extra legend,
%%  Z list={5,7,13,14,15,31,32,33,49,51}]
\end{comment}

<!-- Elenco note a piè di pagina -->

[^1]: Assenza di elettroni dovuta alla **rottura** di un legame. È insieme all'elettrone, un portatore di carica nei semiconduttori.

[^2]: Intervallo di energia interdetto agli elettroni, distanza tra la banda di valenza di conduzione (nei semiconduttori distanti $1\si{eV}$).

[^3]: (penso voglia dire "obiettivo perseguito").

[^4]: Puro, quindi privo di un quantitativo significativo di drogaggio.

[^5]: Oppure densità di ioni, o concentrazione...

[^6]: Nella pratica parto da un blocco puro di silicio, per poi iniettare a *strati* il drogaggio.

[^7]: Fenomeno che si ritrova in natura qualora vi sia uno squilibrio nella distribuzione nello spazio di particelle simili.

[^8]: Svuotata di portatori **mobili**

[^9]: È possibile superarla, ma deve essere fornita una differenza di potenziale **esterna**.

[^10]: Detta anche corrente di deriva (drift), in questo caso i portatori si muovono perché **spinti** dal campo elettrico dovuto allo squilibrio di carica.

[^11]: Il diodo ideale è un dispositivo che lascia passare corrente solo in un senso, con resistenza nulla, e non lascia passare corrente nell’altro senso. Il diodo a giunzione approssima molto bene un diodo ideale, ed è l'elemento circuitale non lineare più importante.

[^12]: Per un aumento di corrente di un fattore mille è sufficiente un aumento di tensione pari a $\SI{0.8}{\volt}$. Infatti viene assunta $\SI{0.6}{\volt}$ come tensione di soglia e $\SI{0.8}{\volt}$ come tensione massima.

[^13]: Dispositivo in grado di convertire una forma di energia in una diversa.

[^14]: Risulta proporzionale al flusso di fotoni che colpiscono il fotodiodo

[^15]: Epossidica, in inglese *epoxy*.

[^16]: Tempo che passa tra la fine dell'influenza esterna (forward bias) ed il momento in cui smette di fluire corrente. È un ritardo causato dalla carenza di lacune ($N_D >> N_A$), causando un accumulo extra di carica in p, la quale sarà rilasciata durante il turnoff.

[^17]: Dal lato p.

[^18]: Infatti sono andate a sostituire le *valvole termoioniche*, o *tubo a vuoto*.

[^19]: Può essere sia un amplificatore di potenza che di tensione.

[^20]: Antiserie indica, per bipoli **polarizzati**, una connessione in serie (quindi un solo punto di contatto), in cui le polarità dei terminali vengono accoppiate per segni uguali

[^21]: Oppure possiamo anche dire che sono due giunzioni p-n poste l'una di seguito all'altra e orientata in senso inverso, andando poi a costituire tre regioni *consecutive*. 

[^22]: Si può esprimere anche come *elettrodo*

[^23]: È una funzione di.

[^24]: In inglese è **gain**.

[^25]: In questo caso la corrente di base è sostituita dall'intensità luminosa. 

[^26]: Un *contatto ohmico* è una giunzione elettrica tra un metallo e un semiconduttore che non ha proprietà rettificanti (non trasforma un segnale alternato in uno continuo). La caratteristica principale è avere una curva corrente-tensione $I-V$ lineare, come prevista dalla legge di Ohm.

[^27]: Ha raggiunto la massima corrente.

[^28]: Quanto *scorrono* facilmente le cariche al suo interno.

[^29]: O n se in un P-MOS.

[^30]: Nel transistore P-MOS accade se la tensione tra drain e source $V_{DS}>0$
