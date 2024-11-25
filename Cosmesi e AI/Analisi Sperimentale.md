# Metriche di Valutazione delle Performance
## Matrice di Confusione
La **matrice di confusione** è uno strumento fondamentale per valutare le prestazioni di algoritmi di classificazione supervisionata, ma il suo utilizzo per il clustering, che è un metodo non supervisionato, richiede un'assegnazione dei cluster ai gruppi reali (se disponibili). Per un algoritmo di clustering, la matrice di confusione viene costruita confrontando le etichette reali (se note) con le etichette di cluster predette. Ogni riga della matrice rappresenta una classe reale, mentre ogni colonna rappresenta un cluster assegnato. La cella $i,j$ indica quante istanze della classe $i$ sono state assegnate al cluster $j$. Da questa matrice si possono derivare metriche come l'accuratezza, la precisione, il richiamo e l'$F1$-score per valutare la qualità dell'assegnazione dei cluster rispetto alle etichette note. Tuttavia, poiché il clustering è intrinsecamente non supervisionato, queste analisi sono possibili solo in presenza di ground truth e non sono sempre applicabili nei casi reali.

-----

## Indici di valutazione dei Clustering
Quando si esegue il confronto tra cluster di dati, è importante considerare le caratteristiche specifiche e i requisiti dei dati stessi. ==Per valutare l'efficacia delle tecniche nell'identificare prodotti chimici dai campioni forniti==, sono stati utilizzato i seguenti indici:
- **Indice di Rand** (**RI**): l'RI è una misura statistica utilizzata nel clustering dei dati per valutare la somiglianza tra due cluster. Il range di questo indice varia da $0$ a $1$, dove $0$ significa che non c'è accordo tra i due cluster di dati su alcuna coppia di punti dati e $1$ significa accordo perfetto, cioè i cluster di dati sono identici. Questa misura conta quante coppie di oggetti sono negli stessi cluster sia in C$_1$ che in C$_2$ (indicate da $n_{11}$) e quante coppie sono in cluster diversi sia in C$_1$ che in C$_2$ (indicate da $n_{00}$), considerando tutte le possibili combinazioni\cite{Gliozzo1, Wagner}. L'Indice di Rand R è calcolato come:

$$R(C_1, C_2) = \frac{2(n_{00} + n_{11})}{n (n -1)} = \frac{n_{00} + n_{11}}{n_{00} + n_{10} + n_{01} + n_{11}}$$

- **Indice di Rand Adjusted** (**ARI**): l'ARI è una versione modificata dell'Indice di Rand ampiamente utilizzata per confrontare i cluster in vari domini. Tiene conto degli accordi casuali e fornisce un punteggio di similarità normalizzato. Mentre l'Indice di Rand è limitato a valori tra $0$ e $1$, l'Indice di Rand Adjusted può generare valori negativi (variando da $-1$ a $1$) se l'indice è inferiore al valore atteso\cite{Wagner};
- **Variazione dell'Informazione** (**VI**): questa misura è comunemente utilizzata nell'analisi dei dati multi-omici in quanto considera l'informazione condivisa e l'entropia (informalmente, l'entropia di un clustering $C$ è una misura dell'incertezza riguardo al cluster di un elemento scelto casualmente) tra due cluster. È una misura della distanza tra due cluster e quantifica la perdita di informazione quando un clustering viene utilizzato per rappresentarne un altro, fornendo approfondimenti sulla somiglianza o dissimilarità tra i cluster \cite{Wagner}. Il range dell'indice VI va da $0$ al valore massimo determinato dal logaritmo del numero di elementi raggruppati;
- **Mutua Informazione Normalizzata** (**NMI**): la NMI è un'altra misura comunemente utilizzata nell'analisi dei dati. L'indice di informazione mutua fornisce un mezzo per quantificare la misura in cui possiamo ridurre l'incertezza riguardo al cluster di un elemento quando possediamo conoscenza del suo cluster in un altro clustering:

$$MI(C_1, C_2) = \sum_{i = 1}^{k} \sum_{j = 1}^{l} P(i, j) \log_2{\frac{P(i, j)}{P(i)P(j)}}$$

dove $P(i, j) = \frac{\vert C_{1i} \cap C_{2j} \vert}{n}$ è la probabilità che un elemento appartenga al cluster $C_i \in C_1$ e al cluster $C_j \in Cluster_2$. Poiché l'informazione mutua non ha un limite superiore, una versione normalizzata è più facile da interpretare:

$$NMI(C_1, C_2) = \frac{MI(C_1, C_2)}{\sqrt{H(C_1)H(C_2)}}$$

dove $H(C_1)$ e $H(C_2)$ sono le entropie associate al clustering $C_1$ e $C_2$. I valori NMI possono variare da $0$ a $1$, con il valore più alto di NMI raggiunto quando $C_1$ è uguale a $C_2$. L'NMI fornisce una misura normalizzata che tiene conto delle differenze intrinseche nelle dimensioni e nelle entropie degli insiemi confrontati\cite{Wagner};
- **Indice di Fowlkes-Mallows**: l'Indice di Fowlkes-Mallows misura la media geometrica della precisione e del richiamo per coppie. Un valore più alto per l'indice di Fowlkes-Mallows indica una maggiore somiglianza tra i cluster e le classificazioni di riferimento\cite{Wagner};
- **Coefficiente di Jaccard**: il Coefficiente di Jaccard è una misura semplice che confronta la somiglianza tra due cluster basandosi sulla presenza o assenza di campioni negli stessi o diversi cluster. È molto simile all'Indice di Rand, tuttavia non considera le coppie di elementi che sono in cluster diversi per entrambi i cluster. Può essere utilizzato come una misura rapida di somiglianza per i cluster\cite{Wagner}. In dettaglio, confronta l'intersezione e l'unione dei punti dati assegnati a ciascun cluster. Fornisce un valore tra $0$ e $1$, con $1$ che indica completa somiglianza e $0$ che indica nessuna somiglianza. Sebbene sia facile da interpretare, è sensibile a piccole dimensioni del campione.

$$J(C_1, C_2) = \frac{\vert C_1 \cap C_2 \vert}{\vert C_1 \cup C_2 \vert} = \frac{n_{11}}{n_{10} + n_{01} + n_{11}}$$

-----

# General Settings
L'applicazione finale di quest'analisi é un modello in grado di trovare una formulazione equivalente ad una data, sostituendo la componente blacklistata con il minor numero possibile di componenti differenti.

Un primo approccio alla risoluzione di questo problema consiste nel definire il concetto di formulazione equivalente. Di nuovo basandomi sull'intuizione che punti vicini nello spazio chimico mantengano questa vicinanza nello spazio fenotipico, la definizione di equivalenza che ho scelto riguarda la composizione qualiquantitativa degli INCI di tale formula.

Fondamentale quindi ottenere come punto di partenza un DataFrame che, a partire da una formula scelta, sia cosí composto:

|          | Componente $1$ | ... | Componente $m$ | TOTALE                  |
| -------- | -------------- | --- | -------------- | ----------------------- |
| INCI $1$ | $x_{1,1}$      | ... | $x_{1,m}$      | $\sum_{i=1}^m x_{1, i}$ |
| INCI $2$ | $x_{2,1}$      | ... | $x_{2, m}$     | $\sum_{i=1}^m x_{2, i}$ |
| ...      | ...            | ... | ...            |                         |
| INCI $n$ | $x_{n,1}$      | ... | $x_{n, m}$     | $\sum_{i=1}^m x_{n, i}$ |

Dove, nella colonna TOTALE, é contenuta la composizione qualiquantitativa degli INCI della formula in questione. Rappresentato ciascuna componente come un vettore delle INCI che lo compongono, è possibile costruire un modello di ottimizzazione che sostituisca l'ingrediente scelto con una combinazione lineare di $n$ ingredienti (con $n \in \mathbb{N}$ fissato ad un valore contenuto) il cui totale di materie prime che compongono questi ingredienti sia il più vicino possibile alla formula qualiquantitativa dell'ingrediente blacklistato.

Nel dettaglio, le variabili $x_j$ del modello decisionale proposto indicano la quantità di ingrediente che andrà inserito nella formula finale in termini di unità di misura di quell'ingrediente.

La traspozione del modello decisionale in codice e cosí strutturata:
- selezione di una formula;
- selezione di un componente interno alla formula da sostituire;
- rimozione di tale componente dal DataFrame sopra rappresentato (per evitare che venga scelto);
- applicazione del modello decisionale.

Poichè la valutazione della bontà di una sostituzione necessita di competenze in ambito chimico non ancora formalizzate, si proporrà un elenco di tali soluzioni in ordine decrescente di vicinanza qualiquantitativa e si sottoporrà ad una figura di riferimento per la valutazione.

-----

Strutturare raccolta dati per testing di GMCEGurobiTest

Una delle tecniche di testing della bontá del modello consiste nel fornire a tale modello solamente la composizione qualiquantitative della formula iniziale e lasciargli libertá totale di scelta nella selezione delle componenti da inserire nella formula.

Questo approccio, nel dettaglio, consiste in un loop di iterazioni del modello di ottimizzazione proposto precedentemente. Ogni iterazione proporrá una nuova soluzione e introdurrá un nuovo vincolo, con lo scopo di escludere la soluzione proposta da tutte le iterazioni successive.

Scelta, ad esempio, la formula '\*ABA009 BASE', avente tale composizione

| fo_codice    | B000016_0 | B000107_0 | B0001501_0 | B000291_0 | B100404_0 | E0001389_0 | total |
| ------------ | --------- | --------- | ---------- | --------- | --------- | ---------- | ----- |
| *ABA009 BASE | 2.0       | 17.4      | 10.0       | 13.1      | 57.4      | 0.1        | 100.0 |

si fornirá al modello la composizione QQ della formula e tramite lo stesso modello di ottimizzazione visto in precedenza, si cercherá di ottimizzare la funzione obiettivo, ovvero minimizzare il numero di componenti scelte.

Risulta evidente dai dati che alla prima iterazione il modello scelga componenti sostanzialmente identiche a quelle originariamente facenti parte della formula selezionata.

| Componente   | Percentuale |
| ------------ | ----------- |
| B000016AF1_0 | 1.99        |
| C1001513_0   | 17.401101   |
| B000112_0    | 9.996377    |
| B000291_1    | 13.09456    |
| B100404CH1_0 | 57.426634   |
| E0001389CH_0 | 0.090057    |
| Totale QQ    | 100.0       |

| Componente | Percentuale |
| ---------- | ----------- |
| B000016_0  | 2.0         |
| B000107_0  | 17.4        |
| B0001501_0 | 10.0        |
| B000291_0  | 13.1        |
| B100404_0  | 57.4        |
| E0001389_0 | 0.1         |
| Totale QQ  | 100.0       |

| Componenti                                             | Initial QQ | Found QQ  |
| ------------------------------------------------------ | ---------- | --------- |
| CERA ALBA                                              | 2.0        | 1.99127   |
| CERA MICROCRISTALLINA                                  | 10.0       | 9.996377  |
| HYDROGENATED MICROCRYSTALLINE WAX                      | 9.4975     | 9.493556  |
| OCTYLDODECANOL                                         | 57.4       | 57.426634 |
| PENTAERYTHRITYL TETRA-DI-T-BUTYL HYDROXYHYDROCINNAMATE | 0.1        | 0.090057  |
| POLYETHYLENE                                           | 17.4       | 17.401101 |
| SYNTHETIC WAX                                          | 3.6025     | 3.601004  |
| Totale Colonna                                         | 100.0      | 100.0     |

==Alla seconda iterazione, il modello 


Questa prima analisi é stata fatta su una formula con un numero relativamente limitato di componenti e di materie prime.

==Se, nel testing, il modello riesce sempre a trovare una sostituzione composta da una singola componente, può essere dovuto alla composizione simile tra quella blacklistata e quella scelta. Quindi è ragionevole confrontare le qq delle due componenti e decidere se escludere componenti con qq troppo simili a quella rimossa

-----

L'utilizzo del modello di clustering ha lo scopo di osservare se formule che descrivono prodotti della stessa categoria sono vicine nello spazio chimico. Se questa proprietá dovesse essere verificata, sarebbe una prima conferma della validitá del risultato ottenuto tramite il modello decisionale.

Il clustering é stato quindi effettuato scegliendo 12 come numero di cluster in quanto il campo ... contiene 12 diverse famiglie di prodotti. Ogni punto nello spazio $n$-dimensionale rappresenta la composizione qualiquantitativa di una data formula.

![[clusters.png]]



-----

# Valutazione della stabilità
==da skippare==

Tools per la stabilità:
[https://www.cir-safety.org/about](https://www.cir-safety.org/about)

[https://echa.europa.eu/](https://echa.europa.eu/)

Esistono diversi strumenti e approcci, sia di intelligenza artificiale che non, che possono aiutarti a valutare la stabilità di una formula cosmetica. La stabilità di una formula è cruciale per garantire che il prodotto rimanga sicuro ed efficace nel tempo, e coinvolge diversi fattori come la compatibilità chimica, la consistenza, il pH, e la resistenza a cambiamenti di temperatura e luce. Gli approcci basati solo sugli INCI (International Nomenclature of Cosmetic Ingredients) di una formula esistono, ma sono più limitati rispetto a quelli che considerano dati chimico-fisici dettagliati. Tuttavia, ci sono strumenti e metodi che sfruttano gli INCI per fare inferenze sulla stabilità e sulla compatibilità degli ingredienti.

- **Cosmetic Analyzer**: Alcuni strumenti online permettono di analizzare la composizione INCI per verificare la compatibilità e la sicurezza degli ingredienti. Questi strumenti possono fornire informazioni sulla potenziale reattività o incompatibilità tra ingredienti basandosi su dati storici;
- **CosDNA**: Questa piattaforma consente di analizzare la formula INCI per identificare ingredienti potenzialmente problematici, ma si concentra più sulla sicurezza e la tollerabilità cutanea che sulla stabilità;
- **Rule-based Systems**: Esistono sistemi basati su regole che utilizzano le descrizioni INCI per determinare se una combinazione di ingredienti è potenzialmente instabile. Questi sistemi si basano su conoscenze preesistenti, come la sensibilità di determinati ingredienti a pH o temperature specifici;
- **Knowledge Graphs e Ontologie**: Alcuni approcci più avanzati possono utilizzare grafi di conoscenza che collegano gli ingredienti INCI con informazioni sulle loro proprietà chimiche, fisiche e biologiche. Questo permette di fare inferenze basate su connessioni note tra ingredienti simili;
- **Similarity Matching**: Alcuni tool cercano di identificare formulazioni simili a quella in esame (basate sugli INCI) e ne valutano la stabilità basandosi su dati storici. Questo approccio si basa sul concetto che formulazioni simili avranno comportamenti di stabilità simili. Alcuni esempi di questi tools sono:
	-  **UL Prospector**: UL Prospector è una piattaforma ampiamente utilizzata dai formulatori di prodotti cosmetici per ricercare ingredienti e formulazioni. La piattaforma consente di confrontare formulazioni basate sugli INCI e offre accesso a una vasta base di dati storici che include informazioni su stabilità e compatibilità degli ingredienti;
	- **Formulator Sample Shop**: Formulator Sample Shop è una risorsa per formulatori che permette di cercare e confrontare ingredienti e formulazioni cosmetiche. La piattaforma offre strumenti per confrontare formulazioni simili e accedere a dati tecnici e di stabilità;
	- **Chemistry Connect (di Azelis)**: Chemistry Connect è una piattaforma che consente ai professionisti di cercare formulazioni esistenti e trovare analoghi sulla base degli INCI. Azelis è un fornitore di ingredienti specializzati e offre accesso a un database esteso di formulazioni cosmetiche con informazioni tecniche e dati di stabilità;
	- **In-cosmetics Formulation Lab**: Questa risorsa è associata agli eventi In-cosmetics e offre accesso a una vasta gamma di formulazioni e ingredienti. Il laboratorio di formulazione permette di trovare formulazioni simili e analizzare la loro stabilità basandosi su esperienze passate e dati storici.

**Complessità delle Interazioni**: La stabilità di una formula spesso dipende da interazioni complesse tra ingredienti, che non possono essere completamente comprese basandosi solo sugli INCI.

https://cosmeticobs.com/en/articles/focus-67/annex-iai-quantitative-and-qualitative-composition-of-the-cosmetic-product-1547

https://link.springer.com/chapter/10.1007/978-981-99-2804-0_7

https://www.mdpi.com/1420-3049/29/2/411

- **Cosmetri**: Un software per la gestione della formulazione cosmetica che permette di creare, analizzare e documentare le formule secondo le normative.