# Chimica Farmaceutica
## Nomenclatura Internazionale degli Ingredienti Cosmetici
La **Nomenclatura Internazionale degli Ingredienti Cosmetici**, o **International Nomenclature of Cosmetic Ingredients** (**INCI**) è una direttiva introdotta dalla Commissione Europea il 1 gennaio 1997 la quale indica una denominazione degli ingredienti contenuti nei prodotti cosmetici.

==Le sostanze chimiche sintetiche e i derivati vegetali che abbiano subito trasformazione chimica, vengono indicati con nome tecnico. I derivati vegetali estratti dalle piante, sono indicati con il nome scientifico (genere e specie) con cui  sono elencati sulla Farmacopea Europea, eventualmente seguito dall'indicazione della parte della pianta da cui sono stati estratti==

==I nomi dei vari ingredienti vengono riportati in etichetta seguendo un ordine che tiene conto della percentuale inserita nel cosmetico, cioè per **concentrazione decrescente**: l'ingrediente più abbondante nei cosmetici è quasi sempre l'acqua, nella nomenclatura INCI riportata in latino "aqua".

==L'etichetta riporta nella prima parte le sostanze strutturali del prodotto ovvero i tensioattivi, gelificanti e umettanti. Nella parte centrale sono riportati i principi attivi e nell'utima parte si leggono i conservanti, i coloranti e i profumi.

==In base alla legge, l'etichetta dei prodotti cosmetici deve recare l'elenco degli ingredienti in ordine decrescente di peso fino all'1%, percentuale sotto la quale possono essere indicati in ordine sparso.==


## Formule Qualiquantitative
Una formula qualiquantitativa è un'espressione che integra aspetti qualitativi e quantitativi per descrivere o rappresentare una realtà o un fenomeno. Gli elementi qualitativi si riferiscono a caratteristiche o proprietà non misurabili numericamente, mentre gli elementi quantitativi riguardano aspetti esprimibili con valori numerici. L'unione di queste due componenti offre una descrizione più completa e dettagliata.**Una formula qualiquantitativa è un'espressione che integra aspetti qualitativi e quantitativi per descrivere o rappresentare una realtà o un fenomeno. Gli elementi qualitativi si riferiscono a caratteristiche o proprietà non misurabili numericamente, mentre gli elementi quantitativi riguardano aspetti esprimibili con valori numerici. L'unione di queste due componenti offre una descrizione più completa e dettagliata.**

-----

# Intelligenza Artificiale e Machine Learning
## Learning Non Supervisionato
Gli algoritmi che utilizzano dati senza alcuna annotazione semantica si dice che operino in modalità di **learning non supervisionato**. Questi algoritmi classificheranno ed organizzeranno gli input sulla base di caratteristiche comuni per cercare di effettuare ragionamenti e previsioni sugli input successivi.
### Clustering

#### KMeans

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