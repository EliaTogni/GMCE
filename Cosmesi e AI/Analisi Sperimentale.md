# Nested Cross Validation

-----

# Metriche di Valutazione delle Performance



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

==Se, nel testing, il modello riesce sempre a trovare una sostituzione composta da una singola componente, può essere dovuto alla composizione simile tra quella blacklistata e quella scelta. Quindi è ragionevole confrontare le qq delle due componenti e decidere se escludere componenti con qq troppo simili a quella rimossa

-----

L'utilizzo del modello di clustering ha lo scopo di osservare se formule che descrivono prodotti della stessa categoria sono vicine nello spazio chimico. Se questa proprietá dovesse essere verificata, sarebbe una prima conferma della validitá del risultato ottenuto tramite il modello decisionale.

Il clustering é stato quindi effettuato scegliendo 12 come numero di cluster in quanto il campo ... contiene 12 diverse famiglie di prodotti. Ogni punto nello spazio $n$-dimensionale rappresenta la composizione qualiquantitativa di una data formula.

![[clusters.png]]



-----

# Valutazione della stabilità

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