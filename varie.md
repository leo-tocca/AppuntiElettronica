**Legge di Ohm:**

\[ V_d = \frac{2}{3} m E \tau \]

con \(\tau =\) tempo medio tra gli urti, dipende dalla temperatura

\[ \mu = \frac{q \tau}{m} \rightarrow V_d = -\mu E \]

\[ \Delta Q = qn \Delta S \Delta x \, (\text{con } \Delta x = v \Delta t) \rightarrow \] carica che attraversa \(\Delta S\) in \(\Delta t\) infinitesimo

\[ j = \frac{q}{\Delta S \Delta t} = qnv \] = densità di corrente, carica che attraversa una sup. nell'unità di tempo

\[ j = \sigma E \]

\[ \sigma = qn \mu \, (\text{conducibilità}) \rightarrow j = qn \mu E = \sigma E \]

\[ I = \int_S j \cdot \vec{n} dS \] = corrente che attraversa la generica sezione di un cilindro a sez. costante.

Ipotesi: j sempre || all'asse del cilindro e \(|j| = \text{cost.} \rightarrow I = jS\)

\(|j| = \text{cost.} \rightarrow E \text{ cost.} \rightarrow V = - \int \vec{E} \cdot d\vec{l} = -lE \rightarrow I = \sigma E S = -\sigma \frac{S}{l} V\)

\[ R = \frac{1}{\sigma} \frac{l}{S} \rightarrow V = -RI \] (segno negativo perché elettroni scorrono in verso opposto al verso convenzionale della tensione)

**Silicio intrinseco:**
\(n_i =\) concentrazione di elettroni liberi o di lacune(dovuta all'agitazione termica) \(\sim 10^{10} \, \text{cm}^{-3}\)
\(v_n = -\mu_n E\) = velocità di deriva per gli elettroni (con \(\mu_n =\) mobilità degli elettroni \(\sim 1350 \, \text{cm}^2/(\text{Vs})\))
\(v_p = \mu_p E\) = velocità di deriva per le lacune (con \(\mu_p =\) mobilità delle lacune \(\sim 550 \, \text{cm}^2/(\text{Vs})\))
Applicando E → j = j_n + j_p = -qn_i v_n + qn_i v_p = qn_i \mu_n E + qn_i \mu_p E

**Silicio drogato n:**
n° elettroni (n) = n_i + N_D ~ N_D (numero di impurità donatrici, \(10^{10} \, \text{cm}^{-3} << N_D << 10^{22} \, \text{cm}^{-3}\))

**Silicio drogato p:**
n° lacune (p) = n_i + N_A ~ N_A (numero di impurtà accettore, \(10^{10} \, \text{cm}^{-3} << N_A << 10^{22} \, \text{cm}^{-3}\))

**Legge di azione di massa:**
Vogliamo conoscere la concentrazione di lacune (elettroni) in presenza di impurtà donatrici (accettore), ovvero avendo fissato a priori il numero di elettroni (lacune).
La ricombinazione è il fenomeno che si ha quando un elettrone e una lacuna si avvicinano abbastanza da riformare il legame covalente spezzato dall'agitazione termica, cessando di esistere come portatori mobili.
R = rnp (tasso di ricombinazione per unità di volume, con r opportuna costante)
L'agitazione termica provoca la rottura dei legami covalenti tra gli atomi di silicio, generando quindi un elettrone e una lacuna mobili per legame spezzato. Per una T fissata il tasso di generazione di coppie elettrone-lacuna G sarà circa lo stesso per il silicio intrinseco e per il silicio drogato (perché N_D e N_A << \(10^{22} \, \text{cm}^{-3} =\) densità di atomi nel silicio intrinseco)
G è necessariamente uguale a R (dal momento che si bilanciano per definizione), quindi
G = R = rnp. Ma nel silicio intrinseco n = p = n_i → G_i = r n_i^2. Dal fatto che G = G_i si ricava la "Legge di azione di massa": np = n_i^2
Questa legge permette di risolvere il problema iniziale, infatti:

- **silicio drogato n:** \(n \approx N_D \rightarrow p \approx \frac{n_i^2}{N_D}\)
- **silicio drogato p:** \(p \approx N_A \rightarrow n \approx \frac{n_i^2}{N_A}\)
<hr><hr>
**Correnti di diffusione:**
jₙ = −qDₚ∂ₓp(x) dove p(x) è la distribuzione di concentrazione delle lacune e Dₚ il coeff. di diff.
jₙ = qDₙ∂ₓn(x) dove n(x) è la distribuzione di concentrazione degli elettroni e Dₙ il coeff. di diff.
In totale quindi in un semiconduttore possono sussistere quattro correnti diverse, ovvero le correnti di deriva e le correnti di diffusione di elettroni e di lacune:

\[ j = qn \mu_n E + qD_n \frac{\partial n(x)}{\partial x} + qp \mu_p E - qD_p \frac{\partial p(x)}{\partial x} \]

\[ \frac{D_n}{\mu_n} = \frac{D_p}{\mu_p} = \frac{kT}{q} \quad (\text{relazione di Einstein}) \quad \text{dove} \quad \frac{kT}{q} = V_T \approx 26 \text{mV (potenziale termico)} \]

**Potenziale di “built-in”:**
Preso un semiconduttore in cui il drogaggio di impurità p (n) non sia costante ma decrescente, la differenza di concentrazione delle lacune farà sì che queste si diffondano nella zona a minore concentrazione, generando uno sbilanciamento di cariche e quindi un campo elettrico. Questo a sua volta genera una corrente di deriva in verso opposto alla corrente di diffusione. Le due correnti in condizione di equilibrio vanno a compensarsi, per cui: \( j_p = qp \mu_p E - qD_p \frac{\partial p(x)}{\partial x} = 0 \)

Applicando la relazione di Einstein si trova pE = Vₜ∂ₓp(x) (*)

Ponendo \( p(x) = N_0 e^{\frac{V_T}{L}} \) si ricava E = −Vₜ/L, ovvero E = cost.
{Ma per la legge di Poisson \(\nabla E = \frac{\rho}{\varepsilon}\), E = cost. significa che non ci sono cariche non compensate (cioè mobili). Eppure esternamente E = 0, quindi ci deve essere una distribuzione di cariche superficiali non compensate, la cui densità si calcola con la legge di Gauss: \(\int_s \vec{E} \cdot \vec{n} dS = \frac{Q}{\varepsilon}\)}

Un campo elettrico costante produce un potenziale crescente che chiamiamo di “built-in”. Questo, essendo sempre compensato dalle cariche superficiali non è direttamente misurabile. Per ricavare la sua espressione integriamo ambo i membri della (*) dopo averla riscritta come \( Edx = V_T \frac{\partial p}{p} \):

\[ \int_{x=0}^{x} Edx = V_T \int_{p(0)}^{p(x)} \frac{dp}{P} \rightarrow v(x) = -V_T \ln \left( \frac{p(x)}{p(0)} \right) \rightarrow p(x) = p(0) e^{\frac{v(x)}{V_T}} \]

L'ultima espressione lega la concentrazione dei portatori in due punti qualsiasi al potenziale tra gli stessi, e vale anche per i portatori n: \( n(x) = n(0) e^{\frac{v(x)}{V_T}} \).

**Diodo:**
\[ i = I_s \left( e^{\frac{v}{V_T}} - 1 \right) \]
se v = 0 → i = 0
se v < 0 → i tende rapidamente a –Is, che è un valore molto piccolo detto corrente di saturazione inversa
se v > 0 → i cresce esponenzialmente
se v >> 2Vₜ → possiamo assumere i ≈ Iₛe^{\frac{v}{V_T}}
La tensione per cui la corrente aumenta rapidamente è circa 0.6V, e si può assumere 0.8V come tensione massima.
**Polarizzazione del diodo:**
Applicando al diodo una tensione tramite un generatore costante e una resistenza (detta “di carico”), si ottiene: V⁺ − V₀ = Riₚ → iₚ = (V⁺ − V₀)/R che è l'espressione della “retta di carico”
Intersecando l'espressione ottenuta con la caratteristica del diodo si ottiene il “punto di lavoro” o “punto critico”, le cui coordinate esprimono l'effettiva tensione ai capi del diodo e la corrente che lo attraversa, e quindi in generale si può assumere v = 0.6V ed iₚ = 0.6V/R
<hr><hr>
**Regione di svuotamento:**
Il funzionamento del diodo dipende dal fenomeno che si manifesta tra zona p e zona n: le differenze
di concentrazione nelle due zone danno origine a due correnti di diffusione una di lacune da p a n e
una di elettroni da n a p. Questa doppia migrazione fa sì che si creino due zone di ioni fissi, negativi
in p e positivi in n. A loro volta questi ioni danno origine a un campo elettrico che si oppone alla
migrazione, fino al raggiungimento dell'equilibrio. Se la concentrazione dei droganti è costante
nelle due zone (giunzione brusca) si crea una regione del tutto priva di portatori mobili.
Poiché prima dello spostamento delle cariche il semiconduttore era neutro, e nessuna carica ha
lasciato il semiconduttore, la neutralità dovrà esserti complessivamente conservata → Qn = Qp →
qNDxN = qNAxP → NDxN = NAxP (**) (la regione di svuotamento sarà più estesa nella regione
meno drogata). Applicando l'eq. di Poisson alle due zone si trova:

\[
\frac{\partial E_n}{\partial x} = \frac{qN_D}{\varepsilon} \quad \frac{\partial E_p}{\partial x} = -\frac{qN_A}{\varepsilon} \rightarrow
\]

\[
E_n(x) = \frac{qN_D}{\varepsilon} x + C_n \quad E_p(x) = -\frac{qN_A}{\varepsilon} x + C_p
\]

Imponendo che le funzioni siano nulle rispettivamente per x = - xn e
x = xp, si determinano Cn e Cp:

\[
E_n(x) = \frac{qN_D}{\varepsilon} x + \frac{qN_D}{\varepsilon} x_n \quad E_p(x) = -\frac{qN_A}{\varepsilon} x + \frac{qN_A}{\varepsilon} x_p
\]

Il campo elettrico nella regione di
svuotamento determina un potenziale

\[
\varphi = \int_{-x_n}^{x_p} E(x) dx = \frac{q}{2 \varepsilon} (N_D x_n^2 + N_A x_p^2)
\]

Usando la (**) possiamo determinare xn e xp:

\[
x_n = \sqrt{\frac{2 \varepsilon}{q} \varphi \frac{N_A}{N_D (N_A + N_D)}} \quad x_p = \sqrt{\frac{2 \varepsilon}{q} \varphi \frac{N_D}{N_A (N_A + N_D)}}
\]

e quindi lo spessore della
regione di svuotamento

\[
w = x_p - x_n = \sqrt{\frac{2 \varepsilon}{q} \varphi \left( \frac{1}{N_A} + \frac{1}{N_D} \right)}
\]

Per un semiconduttore all'equilibrio vale:

\[
n(x) = n(0) e^{\frac{\varphi(x)}{V_T}}
\]

che applicata agli estremi della regione di svuotamento:

\[
n(-x_n) = n(x_p) e^{\frac{\varphi}{V_T}}
\]

permette di calcolare

\[
\varphi = V_T \ln \left( \frac{N_D N_A}{n_i^2} \right)
\]

(***).

**Iniezione di cariche:**
Applicando una tensione vD ai capi del diodo si abbassa il potenziale sulla giunzione, permettendo
così agli elettroni e alle lacune di diffondersi dalla zona n alla zona p e dalla zona p alla zona n,
rispettivamente. Nella zona p e nella zona n, al limite della zona di svuotamento, ci saranno quindi
una concentrazione n(xp) e una concentrazione p(xn) diverse dalle rispettive concentrazioni
all'equilibrio. Per calcolare queste concentrazioni dipendenti da vD ipotizziamo che la distribuzione
di elettroni nel semiconduttore in presenza di una corrente sia circa uguale alla distribuzione
all'equilibrio. Allora possiamo scrivere:

\[
n(x) = n(0) e^{\frac{\varphi(x)}{V_T}}
\]

che applicata agli estremi della regione di
svuotamento dà:

\[
v = V_T \ln \left( \frac{N_D}{n(x_p)} \right)
\]

Facendo l'ulteriore ipotesi che la tensione vD si applichi
interamente alla giunzione possiamo approssimare il potenziale di built-in v con φ - vD.
<hr><hr>
Pertanto:

φ−v_D = V_T ln \left( \frac{N_D}{n(x_p)} \right), \text{ la quale, imponendo la (**), fornisce l'espressione della concentrazione dei portatori n al limite della regione di svuot. nella zona p: } n(x_p) = \frac{n_i^2}{N_A} e^{\frac{v_D}{V_T}} (°).

La concentrazione aumenta esponenzialmente per v_D > 0, per cui si ha una sorta di “iniezione di elettroni” da n a p, che produce la corrente di diffusione alla base del funzionamento del diodo. Per determinare la concentrazione dei portatori n nella zona p, tenuto conto dell'iniezione di cariche (che determina una concentrazione nota n(0) in un lato della zona), scriviamo l'equazione di continuità in un generico volumetto: j_n(x+Δx)ΔyΔz = j_n(x)ΔyΔz . Si deve tenere presente anche della diminuzione degli elettroni a causa della ricombinazione:

j_n(x+Δx)ΔyΔz−j_n(x)ΔyΔz=(−q)∂n/∂tΔyΔz => ∂j_n/∂x+q∂n/∂t=0

∂/∂t n = −rnp; in teoria, ↑η => p↓, ma poiché p ≈ N_A molto grande, la riduzione è trascurabile e: ∂/∂t n = −rnNA = −n/τ. Al numero complessivo degli elettroni contribuisce anche il tasso di generazione: ∂/∂t n = rn_i^2 = rNA(n_i^2/NA) = np0/τ. Sommando le due espressioni : ∂/∂t n = n−n_p0/τ.

Quindi: \frac{1}{q} \frac{\partial j_n}{\partial x} - \frac{n-n_{p0}}{\tau} = 0, \text{ e poiché } j_n = qD_n \partial n/\partial x \Rightarrow \frac{\partial^2 n}{\partial x^2} = \frac{n-n_{p0}}{\tau D_n}. \text{ Definiamo quindi: }

n':=n−n_{p0} => \frac{\partial^2 n'}{\partial x^2} = \frac{n'}{L_n^2}, L_n := \sqrt{\tau D_n} => n'(x)=n'(0)e^{\frac{-x}{L_n}} => \text{ che applicata in } x_p \text{ vale: }

n'(x)=n'(x_p)e^{\frac{(x-x_p)}{L_n}} (°°)

Caratteristica del diodo:
Ipotizziamo che la corrente che attraversa la zona di svuot. sia dovuta principalmente ai portatori n (visto che di solito una delle zone è molto più drogata dell'altra, per es. la zona n). Per via della tensione ai capi v_D ci sarà un'iniezione di elettroni dalla zona n che migreranno per diffusione nella zona p. La corrente di diffusione è proporzionale al gradiente di concentrazione, quindi massima per x = x_p e poi a diminuire fino a 0. Poiché nel diodo la corrente deve essere costante, la corrente di diffusione viene compensata da una corrente di deriva: la corrente sarà unicamente di diffusione per x = x_p e unicamente di deriva lontano dalla giunzione. Per determinare la corrente nel diodo è sufficiente quindi calcolare la corrente di diffusione in x_p:

i = -S_j^{diff} j_n = -qSD_n \frac{\partial n}{\partial x} \bigg|_{x=x_p} = -qSD_n \frac{\partial n'}{\partial x} \bigg|_{x=x_p}, \text{ nella quale imponiamo la (°°): }

i = \frac{qSD_n}{L_n} n(x_p) \frac{n_i^2}{N_A} e^{\frac{v_D}{V_T} - 1} = qS \sqrt{\frac{D_n}{L_n}} \frac{n_i^2}{N_A} e^{\frac{v_D}{V_T} - 1}

MOSFet:
Il capacitore MOS è un sandwich di tre strati sovrapposti, uno di metallo, uno di ossido di silicio (SiO2), e uno di silicio drogato p o n. Allo strato di metallo è applicato un reoforo detto Gate (G) e al silicio un reoforo detto Body (B). Quando tra Gate e Body è applicata una tensione, a seconda del suo valore, possono accadere tre cose:
1/ V_G < 0 => si crea un accumulo di lacune mobili sotto l'ossido
2/ V_G = 0 => si crea una zona di svuot. di ioni fissi negativi sotto l'ossido
3/ V_G > 0 => si crea un canale di cariche negative mobili tra ossido e reg. di svuot.
Nel terzo caso, il canale che si viene a creare è dovuto al campo generato dall'accumulo di cariche positive nel metallo, il quale incurva i livelli energetici come fin sotto l'energia di Fermi della regione drogata, permettendo la conduzione di elettroni (presenti per agitazione termica).
<hr><hr>
Calcolo della tensione di soglia.
Definita φF come EF1 − EF, la tensione necessaria all'inversione sarà 2φF; la tensione di soglia del
capacitore sarà quindi: VTN = 2φF + φOX, con φOX potenziale nell'ossido. Per calcolare φOX scriviamo
la legge di Gauss: ∮ S **E** · **n**dS = ∮ S E ΔS = Q ε dove Q è la carica sul metallo, che deve essere perciò
equivalente alla carica negativa nella regione di svuot. → Q = NADSw → E = qNAW/ε.
Poiché nell'ossido E = cost. → φOX = q NA ε W d . Lo spessore della reg. di svuot. è:
w = √ 2ε q φF 1 NA ≈ √ 2ε q NA (2φF) → VTN = 2φF + d √ 2qNA ε (2φF) con d = spessore dell'ossido
Caratteristica del MOSFet:
Quando la VGS supera VTN sotto l'ossido si accumula una carica mobile Q = −Cox(VGS − VTN), con
Cox = ε WL d , capacità dell'ossido. Questa è pari a quella di un capacitore a facce piane parallele
solo se le cariche sono addensate in prossimità dell'ossido, che è sicuramente vero per le cariche del
Gate, mentre per le cariche nella reg. di svuot. solo se VGS < 0 o di poco > VTN.
Ipotizziamo la densità di carica costante lungo il canale: allora, nel tempo Δt scorrerà rigidamente la
carica ΔQ del tratto Δx, ovvero: iDS = − ΔQ Δt = − ΔQ Δx Δx Δt . Ma ΔQ/Δx è la densità di carica per
unità di lunghezza, ovvero Q/L.
Definendo la capacità per unità di superf. dell'ossido come: C''ox = ε d , possiamo scrivere:
Q L = −C''ox W (VGS−VTN) . Δx/Δt è la velocità di deriva degli elettroni nel canale vn, ed essendo il
canale molto corto rispetto alla larghezza possiamo scrivere: vn = −μnE = −μn ( − vDS L ) .
Definito Kn : = C''ox μn W L → iDS = Kn(VGS−VTN)VDS, espressione che definisce la corrente che scorre
in una resistenza variabile RON = 1 Kn(VGS−VTN) controllata dalla VGS.
Questa espressione non tiene però conto della caduta di tensione a causa della legge di Ohm, ed è
quindi valida solo per vDS piccole. Per grandi tensioni, la tensione lungo il canale sarà v(x), dove
x=0 corrisponde al source e x=XL corrisponde al drain: v(xL) = vDS.
La densità di carica mobile per unità di lunghezza del canale, che prima abbiamo ipotizzato
costante, sarà proporzionale a C''oxW e alla tensione ai capi dell'ossido (vOX(x) = vGS − v(x)) meno
la VTN: Q' = C''oxW(vGS−v(x)−VTN) → iDS = −Q'vn = −C''oxW(vGS−v(x)−VTN)μnE.
Il campo elettrico dovrà necessariamente valere: E = −∂v/∂x(x), essendo v(x) l'unico termine del
potenziale nel canale dipendente da x, quindi: iDS = −C''oxW(vGS−v(x)−VTN)μn∂v/∂x(x) (°°°).
Poiché la corrente deve essere costante nel canale, e quindi densità di carica e velocità di deriva si
devono in modo da mantenere costante il loro prodotto, possiamo scrivere:
iDS 1 L ∫ x= L x0 ∫ x= L x0 C''ox μn W (vGS−v(x)−VTN) ∂v(x) ∂x dx = 1 L ∫ x= L x0 C''ox μn W (vGS−v−VTN) ∂v(x) ∂x dx =
1 L ∫ v= VDS v0 C''ox μn W (vGS−v−VTN) dv → iDS = Kn (VGS−VTN)VDS− 1 2 v2DS con Kn = C''ox μn W L
Per vDS << (VGS − VTN) l'espressione coincide con quella calcolata per piccole tensioni.
Per vDS < (VGS − VTN) l'espressione rappresenta una parabola con vertice in vDS = (VGS − VTN), punto
nel quale la corrente vale iDS = 1 2 Kn(VGS−VTN)2.
<hr><hr>
Per \(V_{DS} > (V_{GS} - V_{TN})\) si dice che il MOSFET è entrato in “saturazione”; in questa regione la corrente
rimane costante al variare della \(V_{DS}\), ha un andamento parabolico dato dall'espressione della corrente
nel massimo ed è quindi funzione della sola \(V_{GS}\).

**Strozzamento del MOSFet:**
In regione lineare la tensione v(x), a partire dal source, cresce con x: l'andamento di v(x) sarà
(integrando entrambi i membri della (∞∞)): \(x = \left(\frac{K_n L}{i_{DS}}\right)\left(-\frac{1}{2}v^2+(v_{GS}-V_{TN})v\right)\).

Utilizzando questa espressione per determinare l'andamento della densità di carica ρ(x) e della
velocità di deriva v(x) si trova che ρ(x) ha un profilo parabolico e diminuisce lungo il canale,
mentre la velocità aumenta iperbolicamente fino a tendere a infinito per x=xmax. In LIN xmax > L, e
diminuisce all'aumentare di VDS fino a che xmax = L per VDS = VGS - VTN. In questo caso però, in
prossimità del drain la velocità di deriva sembra andare a infinito, cosa non fisicamente possibile.
Infatti, in realtà, per grandi campi elettrici la velocità di deriva non è più proporzionale al campo,
ma tende a un valore di saturazione al diminuire della mobilità degli elettroni e di conseguenza
anche la densità di carica non si annulla completamente ma raggiunge un minimo e rimane costante.

**BJT in RAD:**
La condizioni per cui il BJT si trova in regione attiva diretta sono: \(V_{BE} \geq 0.6V\)
\(V_{BC} < 0.6V\).

Si scelgono: \(i_C\) entrante positiva; \(i_B\) entrante positiva; \(i_E\) uscente positiva: \(i_C = i_F\)
\(i_E = i_F + i_B\).

Al confine della reg. di svuot. tra E e B ci sarà una concentrazione di portatori in pari a:
\(n(0) = \left(\frac{n_i^2}{N_B}\right)e^{\frac{V_{BE}}{V_T}}\). Gli elettroni iniettati da E in B sono spinti da B in C per via della polarizzazione
inversa (che impedisce invece alle lacune di migrare da B a C) → n(w) = concentr. di elettroni al confine tra B e C = 0. L'andamento è
approssimabile come lineare (dal momento che lo spessore della base è molto piccolo), quindi la
corrente di diffusione, ovvero iT, dovuta al gradiente di concentr. è:
\(i_T = -qSD_n \frac{\partial n}{\partial x} \approx -qSD_n \frac{n(w) - n(0)}{w} = I_T e^{\frac{V_{BE}}{V_T}} con I_T = \frac{qSD_n}{w}\left(\frac{n_i^2}{N_B}\right)\).

Per determinare iB è sufficiente calcolare il numero di ricombinazioni al secondo nel volume della
base e moltiplicarla per q: \(i_B = q \int rnpdV = qrN_B \int_{x=0}^{x=w} n(x) dx\); ma n(x) segue un andamento
lineare, quindi: \(i_B = qS \frac{n(0)}{2} w = qSw \frac{1}{2 \tau} \left(\frac{n_i^2}{N_B}\right) e^{\frac{V_{BE}}{V_T}} con \tau = \frac{1}{rN_B}\).

Se dividiamo iC per iB: \(\frac{i_C}{i_B} = \frac{2D_n}{rw^2} \rightarrow i_C = \beta_F i_B con \beta_F = 2 \left(\frac{L_n}{w}\right)^2 dove L_n = \sqrt{\tau D_n}\).

**Modello linearizzato del MOSFet:**
*Maiuscole → Grandezze costanti (fissate dalla polarizz.)*
*Minuscole → Grandezze variabili (generalmente il segnale)*
*Pedice minuscolo → segnale abbastanza piccolo da appross. la funz. di trasf. con Taylor arrestato al primo ordine*

Sviluppando la iDS(VGS, VDS) con Taylor al prim'ordine si ottiene:
\(i_{DS} = i_{DS}(V_{GS}, V_{DS}) + \frac{\partial i_{DS}}{\partial V_{GS}} \bigg|_{V_{GS} = V_{GS}, V_{DS} = V_{DS}} v_{gs} + \frac{\partial i_{DS}}{\partial V_{DS}} \bigg|_{V_{GS} = V_{GS}, V_{DS} = V_{DS}} v_{ds}\) cioè: \(i_d = \frac{\partial i_{DS}}{\partial V_{DS}} \bigg|_{V_{GS} = V_{GS}, V_{DS} = V_{DS}} v_{ds} + \frac{\partial i_{DS}}{\partial V_{GS}} \bigg|_{V_{GS} = V_{GS}, V_{DS} = V_{DS}} v_{gs}\)
<hr><hr>
Calcoliamo la derivata di i_DS rispetto a v_GS: in saturazione: i_DS = \frac{K_n}{2} (v_{GS} - V_{TN})^2 (1 + \lambda v_{DS}) \rightarrow

\frac{\partial i_{DS}}{\partial v_{GS}} \bigg|_{v_{GS} = v'_{GS} \atop v_{DS} = v'_{DS}} = K_n (V_{GS} - V_{TN}) (1 + \lambda V_{DS}) \approx g_m := K_n (V_{GS} - V_{TN}) \text{ transconduttanza del FET} ;

Calcoliamo la derivata di i_DS rispetto a V_DS:

\frac{\partial i_{DS}}{\partial v_{DS}} \bigg|_{v_{GS} = v'_{GS} \atop v_{DS} = v'_{DS}} = \lambda \frac{K_n}{2} (V_{GS} - V_{TN})^2 = \frac{1}{r_o} := \lambda I_{DS} \text{ resistenza di drain} ; quindi: i_d = g_m v_{gs} + \frac{v_{ds}}{r_o} .

A_v = \frac{v_{ds}}{v_{gs}} = -g_m r_o \text{ massimo guadagno di tensione ottenibile}

Calcoliamo quando è verificata la condizione per cui il modello linearizzato è applicabile, cioè che lo sviluppo di Taylor della funzione di trasferimento del FET in SAT è arrestabile al 1° ordine:

i_{DS} = \frac{K_n}{2} (V_{GS} - V_{TN})^2 = \frac{K_n}{2} (V_{GS} + v_{gs} - V_{TN})^2 = \frac{K_n}{2} (V_{GS} - V_{TN})^2 \left( 1 + \frac{v_{gs}}{V_{GS} - V_{TN}} \right)^2 =

\frac{K_n}{2} (V_{GS} - V_{TN})^2 \left( 1 + 2 \frac{v_{gs}}{V_{GS} - V_{TN}} + \left( \frac{v_{gs}}{V_{GS} - V_{TN}} \right)^2 \right) .

La condizione è quindi che:

\left( \frac{v_{gs}}{V_{GS} - V_{TN}} \right)^2 \ll 2 \left( \frac{v_{gs}}{V_{GS} - V_{TN}} \right) \rightarrow v_{gs} \ll 2 (V_{GS} - V_{TN}) \rightarrow v_{gs} < 2 (V_{GS} - V_{TN}) / 10 .

Modello linearizzato del BJT:
i_C = I_C + i_c , V_{CE} = V_{CE} + v_{ce} . Sviluppiamo e arrestiamo al prim'ordine
i_B = I_B + i_b , V_{BE} = V_{BE} + V_{be} .

otteniamo: i_c = \frac{\partial i_C}{\partial v_{BE}} \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} v_{be} + \frac{\partial i_C}{\partial v_{CE}} \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} v_{ce} e i_b = \frac{\partial i_B}{\partial v_{BE}} \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} v_{be} + \frac{\partial i_B}{\partial v_{CE}} \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} v_{ce} .

Calcoliamo la derivata di i_c rispetto a v_{BE}:

\frac{\partial i_C}{\partial v_{BE}} \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} = \frac{\partial}{\partial v_{BE}} I_C e^{\frac{V_{BE}}{V_T}} \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} = \frac{I_C}{V_T} e^{\frac{V_{BE}}{V_T}} = g_m := \frac{I_C}{V_T} \text{ con } I_T = \frac{qSD_n}{w} \left( \frac{n_i^2}{N_B} \right) .

In teoria anche lo spessore della base w varia con V_{BE}, la quale riduce la regione di svuotamento e quindi fa aumentare lo spessore della base, ma essendo la giunzione polarizzata direttamente, la regione è piccola e varia di poco con la V_{BE}, quindi la dipendenza è trascurabile.
Per calcolare la derivata di i_c rispetto a v_{CE}, notiamo che, fissata la V_{BE}, la dipendenza di i_c da V_{CE} (dovuta all'effetto early) è circa lineare e la sua pendenza (ovvero la derivata) è:

\frac{\partial i_C}{\partial v_{CE}} \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} = \frac{I_C}{V_{CE} + V_A} \approx \frac{1}{r_o} = \frac{I_C}{V_A} .

Calcoliamo la derivata di i_b rispetto a v_{BE}:

\frac{\partial i_B}{\partial v_{BE}} \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} = \frac{\partial}{\partial v_{BE}} I_B e^{\frac{V_{BE}}{V_T}} \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} = \frac{I_B}{V_T} e^{\frac{V_{BE}}{V_T}} = \frac{I_C}{\beta_F V_T} = \frac{1}{r_{\pi}} := \frac{g_m}{\beta_F} \text{ con } I_{B0} = \frac{qS w}{2 \tau} \left( \frac{n_i^2}{N_B} \right) .

Calcoliamo la derivata di i_B rispetto a v_{CE}; l'unico termine dipendente da v_{CE} è w, quindi:

\frac{\partial i_B}{\partial v_{CE}} \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} = \frac{qS}{2 \tau} \left( \frac{n_i^2}{N_B} \right) \frac{\partial}{\partial v_{CE}} w \bigg|_{v_{BE} = V'_{BE} \atop v_{CE} = V'_{CE}} .
<hr><hr>
Per determinare la derivata di w ricalcoliamo la derivata di i\_C rispetto a v\_{CE} senza trascurare la dipendenza di w da v\_{CE}:

i\_C = \frac{qSD\_n}{w} \left( \frac{n\_i^2}{N\_B} \right) e^{\frac{v\_{BE}}{V\_T}} \rightarrow \frac{\partial i\_C}{\partial v\_{CE}} \bigg| \_{v\_{BE} = V\_{BE} \\ v\_{CE} = V\_{CE}} = \frac{qSD\_n}{w^2} \left( \frac{n\_i^2}{N\_B} \right) e^{\frac{V\_{BE}}{V\_T}} \frac{\partial w}{\partial v\_{CE}} \bigg| \_{v\_{BE} = V\_{BE} \\ v\_{CE} = V\_{CE}} = -I\_C \frac{1}{w\_0} \frac{\partial w}{\partial v\_{CE}} \bigg| \_{v\_{BE} = V\_{BE} \\ v\_{CE} = V\_{CE}},

con w\_0 larghezza della base nel punto di lavoro. Inserendo l'espressione trovata precedentemente per la i\_C: \frac{\partial i\_C}{\partial v\_{CE}} \bigg| \_{v\_{BE} = V\_{BE} \\ v\_{CE} = V\_{CE}} = \frac{I\_C}{V\_A} \rightarrow -I\_C \frac{1}{w\_0} \frac{\partial w}{\partial v\_{CE}} \bigg| \_{v\_{BE} = V\_{BE} \\ v\_{CE} = V\_{CE}} = \frac{I\_C}{V\_A} \rightarrow \frac{\partial w}{\partial v\_{CE}} \bigg| \_{v\_{BE} = V\_{BE} \\ v\_{CE} = V\_{CE}} = -\frac{w\_0}{V\_A} \rightarrow \frac{\partial i\_B}{\partial v\_{CE}} \bigg| \_{v\_{BE} = V\_{BE} \\ v\_{CE} = V\_{CE}} = \frac{I\_B}{V\_A} = \frac{1}{\beta\_F} \frac{I\_C}{V\_A} = \frac{1}{\beta\_F r\_o}. In definitiva: i\_c = g\_m v\_{be} + \frac{v\_{ce}}{r\_o} e i\_b = \frac{v\_{be}}{r\_\pi} - \frac{v\_{ce}}{\beta\_F r\_o} \approx \frac{v\_{be}}{r\_\pi}

A\_{vv} = \frac{v\_{ce}}{v\_{be}} = -g\_m r\_o = \frac{V\_A}{V\_T}. Calcoliamo quando è verificata la condizione per cui il modello linearizzato è applicabile, cioè che lo sviluppo di Taylor della funzione di trasferimento del BJT in RAD è arrestabile al 1° ordine:

i\_C = I\_C e^{\frac{v\_{be}}{V\_T}} = I\_T e^{\frac{v\_{BE} + v\_{be}}{V\_T}} = I\_T e^{\frac{V\_{BE}}{V\_T}} \left( 1 + \frac{v\_{be}}{V\_T} + \frac{1}{2} \left( \frac{v\_{be}}{V\_T} \right)^2 + ... \right); la condizione è quindi verificata se: \frac{1}{2} \left( \frac{v\_{be}}{V\_T} \right)^2 \ll \frac{v\_{be}}{V\_T} \rightarrow v\_{be} \ll 2V\_T \approx 50mV
