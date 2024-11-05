# Chimica Farmaceutica
## Nomenclatura Internazionale degli Ingredienti Cosmetici (INCI)

La **Nomenclatura Internazionale degli Ingredienti Cosmetici**, nota anche come **International Nomenclature of Cosmetic Ingredients** (**INCI**), è una direttiva introdotta dalla Commissione Europea il 1º gennaio 1997 che stabilisce la denominazione standardizzata degli ingredienti presenti nei prodotti cosmetici. Ogni nome INCI rappresenta un identificatore univoco per ciascun ingrediente cosmetico, assicurando così una comunicazione uniforme e chiara ai consumatori. Secondo la normativa vigente, ogni prodotto cosmetico immesso sul mercato è obbligato a riportare in etichetta l’elenco degli ingredienti utilizzando la denominazione INCI.

Gli ingredienti sono elencati sull'etichetta seguendo un ordine basato sulla **concentrazione decrescente**: gli ingredienti più presenti nel prodotto sono riportati all'inizio, mentre quelli in percentuali inferiori seguono in ordine decrescente. Di solito, l’ingrediente principale nei cosmetici è l’acqua, indicata in latino come “aqua” nella nomenclatura INCI.

L’elenco degli ingredienti è suddiviso in sezioni che riflettono la funzione di ciascuna sostanza:
- Nella prima parte sono riportate le **sostanze strutturali** del prodotto, come tensioattivi, gelificanti e umettanti;
- Nella parte centrale figurano i **principi attivi**, ovvero le sostanze con specifiche proprietà funzionali;
- L’ultima parte dell’elenco include i **conservanti**, i **coloranti** e le **fragranze**.

La normativa stabilisce inoltre che gli ingredienti devono essere indicati in ordine decrescente di peso fino alla concentrazione dell'1%; al di sotto di tale soglia, possono essere elencati in ordine sparso.

Le denominazioni INCI possono seguire diversi formati a seconda del trattamento subito dagli ingredienti:
- Gli ingredienti indicati in **lingua latina** con il proprio nome scientifico (genere e specie), seguito eventualmente dalla specifica della parte della pianta utilizzata, sono inseriti nel prodotto in forma pura e naturale, senza trattamenti (ad esempio, **Maris Aqua** per l’acqua di mare nella sua forma naturale e non trattata);
- Gli ingredienti che compaiono con **nome botanico in latino** seguito da una descrizione in inglese rappresentano derivati naturali di origine vegetale (es. **Aloe Barbadensis Leaf Juice**: _Aloe Barbadensis_ indica la pianta di Aloe Vera, mentre _Leaf Juice_ specifica che si tratta del succo estratto dalle foglie);
- Gli ingredienti riportati **in lingua inglese** con la rispettiva denominazione tecnica sono stati sottoposti a processi di trasformazione chimica prima dell’inclusione nella formulazione (ad esempio, **Xanthan Gum**, un polisaccaride ottenuto dalla fermentazione di microrganismi naturali). Fa eccezione la denominazione **_Parfum_** (fragranza), che viene riportata in francese;
- Gli ingredienti elencati in **formato alfanumerico** indicano coloranti, classificati secondo il registro internazionale del **Color Index International** (ad esempio, **Ci 77491** indica un colorante minerale rosso, noto anche come triossido di ferro).

-----

## Formule Qualiquantitative
Una formula qualiquantitativa è un'espressione che integra aspetti qualitativi e quantitativi per descrivere o rappresentare una realtà o un fenomeno. Gli elementi qualitativi si riferiscono a caratteristiche o proprietà non misurabili numericamente, mentre gli elementi quantitativi riguardano aspetti esprimibili con valori numerici. L'unione di queste due componenti offre una descrizione più completa e dettagliata.

-----

# Ricerca Operativa

## Programmazione Matematica
La programmazione matematica è un ramo della ricerca operativa che si occupa di formulare e risolvere problemi in cui è necessario prendere decisioni ottimali rispetto a un obiettivo specifico, come massimizzare i profitti o minimizzare i costi, rispettando una serie di vincoli.
## Programmazione Lineare
La Programmazione Lineare utilizza un modello matematico per descrivere il problema in questione. L’aggettivo **lineare** indica che tutte le funzioni matematiche in questo modello devono essere funzioni lineari. La parola **programmazione** qui non si riferisce alla programmazione informatica ma è, piuttosto, un sinonimo di pianificazione. Pertanto, la Programmazione Lineare riguarda la pianificazione delle attività per ottenere un risultato ottimale, cioè un risultato che raggiunga nel miglior modo possibile l’obiettivo specificato (secondo il modello matematico) tra tutte le alternative possibili.

==aggiungere sheldon ross a bibliografia

Un problema si dice di Programmazione Lineare quando:
- le variabili hanno un dominio continuo;
- i vincoli sono equazioni e disequazioni lineari;
- la funzione obiettivo è una funzione lineare delle variabili

Nella sua formulazione generale, un problema di Programmazione Lineare è espresso come segue:

$\text{max/min} \; z = c^T x$

soggetto ai vincoli:

$A x \geq b$
$x \geq 0$

dove $c$ è un vettore dei coefficienti dell’obiettivo, $x$ è il vettore delle variabili decisionali, $A$ è la matrice dei coefficienti dei vincoli e $b$ è il vettore dei termini noti.

I vincoli possono assumere la forma di disuguaglianze del tipo maggiore o uguale, minore o uguale, oppure di uguaglianze. Inoltre, alcune variabili possono essere limitate a valori non negativi.

Ogni soluzione $x$ puó essere interpretata, essendo un assegnamento di valore alle variabili, come un punto in uno spazio continuo ad $n$ dimensioni dove $n$ è il numero di variabili nel modello.

Nello spazio $n$-dimensionale delle soluzioni, ogni soluzione è considerabile come un punto in tale spazio ed ogni vincolo di uguaglianza è considerabile come un iperpiano (poiché è lineare). Se il vincolo è di disuguaglianza, allora esso corrisponde ad un semispazio, cioè non solo ai punti sull’iperpiano ma anche a quelli che giacciono da una parte dell’iperpiano.

Il sistema dei vincoli impone che ciascuna condizione sia rispettata, il che equivale a considerare l'intersezione di diversi semispazi. Questa intersezione definisce un poliedro. La proprietà principale di un poliedro è la **convessità**, ovvero la caratteristica per cui, dati due punti qualsiasi all'interno del poliedro, il segmento che li congiunge rimane interamente contenuto all'interno del poliedro stesso. Di conseguenza, anche i semispazi che lo compongono sono convessi.

Esistono vari tipi di poliedri. Un poliedro limitato si chiama politopo. può essercene anche uno illimitato, tale per cui se parto da un punto interno al poliedro, esiste una direzione verso la quale non incontro mai la frontiera del poliedro.
Inoltre esiste un poliedro vuoto, definito da vincoli combinati in maniera tale da impedire l’esistenza di una qualsiasi soluzione ammissibile.

Nel discreto ci sono varie classi di problemi particolari nella Programmazione Lineare Intera:
- Integer Programming (IP): le variabili possono assumere solamente valori interi;
- Binary Programming (BP): le variabili possono assumere solo valori 0 e 1;
- Mixed-Integer Programming (MIP): esistono vari tipi di variabili (intere, continue o binarie) nello stesso problema.
- \item CO: combinatory optimization -> ci sono delle variabili che indicano di solito elementi di un insieme per cui il numero di soluzioni cresce come il numero di sottoinsiemi dell'insieme dato( in modo combinatorio quindi)

-----

# Intelligenza Artificiale e Machine Learning
## Learning Non Supervisionato
Gli algoritmi che utilizzano dati senza alcuna annotazione semantica si dice che operino in modalità di **learning non supervisionato**. Questi algoritmi classificheranno ed organizzeranno gli input sulla base di caratteristiche comuni per cercare di effettuare ragionamenti e previsioni sugli input successivi.
### Clustering
==In statistica, il **clustering** o **analisi dei gruppi** è un insieme di tecniche di analisi multivariata dei dati volte alla selezione e raggruppamento di elementi omogenei in un insieme di dati.== 

==Given a training set, the classifier generated by NN is based on the following simple rule: predict every point in the training set with its own label, and predict any other point with the label of the point in the training set which is closest to it.

#### KMeans
L’algoritmo **k-means** è un metodo di clustering iterativo non supervisionato utilizzato per partizionare un insieme di dati in $k$ cluster, dove $k$ è un numero predefinito di cluster scelto dall’utente. L’obiettivo dell’algoritmo è minimizzare la somma delle distanze al quadrato tra ciascun punto e il **centroide** del cluster a cui appartiene, riducendo così la varianza all'interno di ciascun cluster.

Il processo inizia con la selezione casuale di $k$ centroidi iniziali, uno per ciascun cluster. Successivamente, l'algoritmo alterna due fasi principali:
1) **Assegnazione dei punti ai cluster**: ciascun punto dati viene assegnato al cluster il cui centroide è il più vicino, misurato generalmente tramite la distanza euclidea;
2) **Aggiornamento dei centroidi**: per ciascun cluster, viene ricalcolato il centroide come media aritmetica dei punti assegnati al cluster stesso.

Queste due fasi vengono ripetute fino al raggiungimento di una **condizione di arresto**, che può essere definita dal raggiungimento di un numero massimo di iterazioni o dal caso in cui le assegnazioni dei punti ai cluster non cambiano più tra un'iterazione e l'altra (ovvero, i centroidi si stabilizzano).

L'algoritmo k-means è sensibile alla scelta dei centroidi iniziali, motivo per cui vengono spesso utilizzate tecniche apposite per migliorarne l'inizializzazione e ottenere risultati più stabili.

-----

## Learning Supervisionato
Gli algoritmi che risolvono una learning task basata su dati annotati semanticamente (ad esempio, documenti annotati con il loro argomento o immagini annotate con gli oggetti che contengono) si dice che operino in modalità di **learning supervisionato**

### Artificial Neural Networks
Le **Artificial Neural Networks** (ANNs) sono una grande e complessa classe di predittori applicabili a una varietà di campi, data la loro potente capacità in compiti come classificazione, regressione e predizione di sequenze.

Una Rete Neurale è solitamente rappresentata come un grafo $G = \langle V , E \rangle$, dove $V$ è l'insieme finito di vertici o nodi e $E$ è l'insieme finito di archi pesati. I vertici $v \in V$ sono chiamati **neuroni** o unità e gli archi $e \in E$ sono chiamati **connessioni**.

Ogni neurone prima calcola il prodotto dei pesi degli archi in entrata con i corrispondenti input in entrata e poi applica una funzione di attivazione su di esso.

Farò riferimento e considererò solo **Feed Forward Neural Netwkors** (per ora, potrei usare delle hopfield più avanti),  ovvero modelli in cui non ci sono cicli o loop nella rappresentazione a grafo della rete. Il termine Feed Forward si riferisce al fatto che il calcolo può essere trasmesso solo lungo le connessioni direzionali e che l'output di un livello diventa l'input del livello successivo\cite{Kruse}.

#### Multi Layer Neural Network
La forma più semplice di Feed Forward Neural Network è la Multi-Layer Neural Network, una classe di reti neurali artificiali caratterizzate dalla loro architettura a strati, costituita da più nodi interconnessi organizzati in tre principali tipi di strati:
- **Input Layer**: questo tipo di strato rappresenta il punto di ingresso di una rete neurale. La sua forma dovrebbe essere uguale a quella degli input. È responsabile di propagare l'input senza alcuna modifica allo strato successivo. I nodi in questo tipo di strato non hanno archi in entrata;
- **Output Layer**: questo tipo di strato è responsabile di restituire l'output della rete. I nodi in questo tipo di strato non hanno archi in uscita;
- **Hidden Layer**: questo tipo di strato comprende tutti gli strati tra quello di input e quello di output. Tutti i nodi in questo tipo di strato hanno sia archi in entrata che in uscita.

-----