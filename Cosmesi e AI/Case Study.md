# Struttura del Dataset

| ta_nomedb                         | ta_descri                          | ta_esterna |     |
| --------------------------------- | ---------------------------------- | ---------- | --- |
| __cbl_formumast_inciestesa        | Inciestesa                         | 0          |     |
| __cbl_regoleinci                  | Regoleinci                         | 0          |     |
| __cbl_formumast_stampe            | Formumast_stampe                   | 0          |     |
| __cbl_formumast_incistampe        | Inci Stampe                        | 0          |     |
| __cbl_connessioni_impformule_dett | Importa formule subquery           | 0          |     |
| __cbl_connessioni_impformule      | Connessioni_impformule             | 0          |     |
| __cbl_formumast_fasi              | Formumast_fasi                     | 0          |     |
| __cbl_connessioni                 | Lista connessioni                  | 0          |     |
| __cbl_importauto_dett             | Importauto_dett                    | 0          |     |
| __cbl_import_mast                 | Import_mast                        | 0          |     |
| __cbl_import_dett                 | Import_dett                        | 0          |     |
| __cbl_importauto                  | Importazioni automatiche           | 0          |     |
| __cbl_formumast_trasformazioni    | formumast_trasformazioni           | 0          |     |
| __cbl_tempisync                   | Tempi di sincronizzazione          | 0          |     |
| __cbl_formumast_inci              | Inci                               | 0          |     |
| __cbl_diary                       | Diary                              | 0          |     |
| __cbl_prodotti_alternativi        | Prodotti alternativi               | 0          |     |
| __cbl_prodotti_fornitori          | Prodotti/fornitori                 | 0          |     |
| __cbl_produttori                  | Produttori                         | 0          |     |
| __cbl_fornitori                   | Fornitori                          | 0          |     |
| __cbl_clienti_brand_blacklist     | Black Listi Brand                  | 0          |     |
| __cbl_metallipesanti              | Metalli pesanti                    | 0          |     |
| __cbl_formumast_componenti        | Componenti                         | 0          |     |
| __cbl_formumast_metalli_dett      | Metalli formula check              | 0          |     |
| __cbl_formumast_metalli           | Check Metalli                      | 0          |     |
| __cbl_clienti_metalli             | Metalli pesanti                    | 0          |     |
| __cbl_clienti_brand_metalli       | Metalli pesanti                    | 0          |     |
| __cbl_clienti_brand               | Brand                              | 0          |     |
| __cbl_sheet_uni_campi             | Campi foglio excel                 | 0          |     |
| __cbl_tmplexcel_sheet_uni         | Dettaglio Foglio                   | 0          |     |
| __cbl_tmplexcel_sheet             | Fogli Excel                        | 0          |     |
| __cbl_tmplexcel                   | Template EXCEL                     | 0          |     |
| __cbl_funzione_kiko               | Funzione KIKO                      | 0          |     |
| __cbl_origine_kiko                | Origine KIKO                       | 0          |     |
| __cbl_aiuti                       | Aiuti                              | 0          |     |
| __users                           | Users                              | 1          |     |
| __cbl_clienti_blacklist           | Black Listi Cliente                | 0          |     |
| __cbl_clienti                     | Clienti                            | 0          |     |
| __cbl_checkmast_blacklist         | Elenco Black List                  | 0          |     |
| __cbl_bldett_controlliwarning     | Controlli BL Warning               | 0          |     |
| __cbl_checkinci_dett              | Check Inci dettaglio               | 0          |     |
| __cbl_bldett_controlli            | Controlli BL                       | 0          |     |
| __cbl_checkprel_dett              | Check preliminare formula dettagli | 0          |     |
| __cbl_config                      | Configurazione                     | 0          |     |
| __cbl_checkprel                   | Check preliminare formula          | 0          |     |
| __cbl_campicontrollo              | Campi controllo check              | 0          |     |
| __cbl_gruout                      | Gruppi output                      | 0          |     |
| __cbl_checkinci                   | Check Inci                         | 0          |     |
| __cbl_checkdett                   | Dettaglio gruppi                   | 0          |     |
| __cbl_ingredienti                 | Ingredienti                        | 0          |     |
| __cbl_checkmast                   | Check                              | 0          |     |
| __cbl_prodotti_cmp                | Prodotti Composizione              | 0          |     |
| __cbl_prodotti                    | Prodotti                           | 0          |     |
| __cbl_formudett                   | Componenti Formula                 | 0          |     |
| __cbl_formumast                   | Formula                            | 0          |     |
| __cbl_bldett                      | Dettaglio Black List               | 0          |     |
| __cbl_blmast                      | Black List                         | 0          |     |
| __cbl_aziende                     | Aziende                            | 0          |     |
| __cbl_menuparam                   | Menù Parametri                     | 0          |     |
| __cbl_menugruppi                  | Menù Dettaglio Gruppi Utenti       | 0          |     |
| __cbl_menu                        | Menù                               | 0          |     |
| __cbl_utenti                      | Utenti                             | 0          |     |
| __cbl_gruute                      | Gruppi Utenti                      | 0          |     |
| __cbl_progressivi                 | Progressivi                        | 0          |     |
| __cbl_logemail                    | Log Email                          | 0          |     |
| __cbl_debug                       | Progressivi                        | 0          |     |
| __cbl_sysftp                      | Configurazione FTP Pacchetto       | 0          |     |

## Schema ER


| Tabella                          | Collegata con                | Join                | Collegamento                                                                |
| -------------------------------- | ---------------------------- | ------------------- | --------------------------------------------------------------------------- |
| jos_cbl_bldett                   | jos_cbl_blmast               | INNER JOIN          | jos_cbl_bldett.id_master=jos_cbl_blmast.id                                  |
| jos_cbl_formumast                | jos_cbl_prodotti             | ==INNER JOIN==      | jos_cbl_formumast.id_prodotto=jos_cbl_prodotti.id                           |
| jos_cbl_formudett                | jos_cbl_formumast            | ==INNER JOIN==      | jos_cbl_formudett.id_master=jos_cbl_formumast.id                            |
| jos_cbl_formudett                | jos_cbl_prodotti             | ==INNER JOIN==      | jos_cbl_formudett.id_componente=jos_cbl_prodotti.id                         |
| jos_cbl_formumast_inciestesa     | jos_cbl_formumast            | ==INNER JOIN==      | jos_cbl_formumast_inciestesa.id_master=jos_cbl_formumast.id                 |
| jos_cbl_formumast_inciestesa     | jos_cbl_prodotti             | ==INNER JOIN==      | jos_cbl_formumast_inciestesa.id_prodotto=jos_cbl_prodotti.id                |
| jos_cbl_formumast_inciestesa     | jos_cbl_prodotti_cmp         | ==INNER JOIN==      | jos_cbl_formumast_inciestesa.id_prodotto_cmp=jos_cbl_prodotti_cmp.id        |
| jos_cbl_formumast_inciestesa     | jos_cbl_formumast_inciestesa | ==LEFT OUTER JOIN== | jos_cbl_formumast_inciestesa.id=jos_cbl_formumast_inciestesa.id_inci_master |
| jos_cbl_formumast_inci           | jos_cbl_formumast            | ==INNER JOIN==      | jos_cbl_formumast_inci.id_master=jos_cbl_formumast.id                       |
| jos_cbl_formumast_inci           | jos_cbl_prodotti             | ==LEFT OUTER JOIN== | jos_cbl_formumast_inci.id_prodotto=jos_cbl_prodotti.id                      |
| jos_cbl_formumast_inci           | jos_cbl_prodotti_cmp         | ==LEFT OUTER JOIN== | jos_cbl_formumast_inci.id_prodotto_cmp=jos_cbl_prodotti_cmp.id              |
| jos_cbl_formumast_inci           | jos_cbl_formumast_inci       | ==LEFT OUTER JOIN== | jos_cbl_formumast_inci.id_inci_master=jos_cbl_formumast_inci.id             |
| jos_cbl_formumast_trasformazioni | jos_cbl_formumast            | INNER JOIN          | jos_cbl_formumast_trasformazioni.id_master=jos_cbl_formumast.id             |
| jos_cbl_prodotti_cmp             | jos_cbl_prodotti             | ==INNER JOIN==      | jos_cbl_prodotti_cmp.id_master=jos_cbl_prodotti.id                          |


![[ERCosmesi.drawio.png]]

-----

# Tabelle
### Formumast
La tabella descrive le caratteristiche del prodotto ottenuto dalla formula.

| Attribute      | Meaning                                                                                                                                                                          |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id             | Identifier della tupla                                                                                                                                                           |
| fo_codice      | codice indicativo della formula. Appare nella pagina dei qq nel campo **Codice**. E' ottenuto (non sempre purtroppo) tramite concatenazione di fo_texture, fo_colore e fo_stile. |
| fo_descri      | Stringa che descrive il prodotto ottenuto dalla formula (==descrizione inconsistente==). Appare nella pagina dei qq nel campo **Descrizione**.                                   |
| id_prodotto    | Appare nella pagina dei qq nel campo **Prodotto**. E' ottenuto (non sempre purtroppo) tramite concatenazione di codice e descrizione.                                            |
| codiceext      | Serve alla GMCE per gli import, inutile per me.                                                                                                                                  |
| codazie        | Questo campo ha sempre valore **More**.                                                                                                                                          |
| fo_versione    | Intero che indica la versione della formula. Appare nella pagina dei qq nel campo **Descrizione**.                                                                               |
| fo_stato       | Stringa che indica lo stato della formula. Può essere **In revisione**, **Approvato**, **Obsoleto**. Appare nella pagina dei qq nel campo **Stato**.                             |
| fo_unimis      | G, g, NAN, kg                                                                                                                                                                    |
| fo_texture     | Appare nella pagina dei qq nel campo **Texture**.                                                                                                                                |
| fo_colore      | Appare nella pagina dei qq nel campo **Colore**.                                                                                                                                 |
| fo_stile       | Appare nella pagina dei qq nel campo **Stile**.                                                                                                                                  |
| id_formorigine | Da ignorare, tutti a zero.                                                                                                                                                       |


-----

### Formumast_inci
La tabella descrive le diverse INCI che compongono la formula QQ del prodotto.

| Attribute       | Meaning                                                                                                                                                                                              |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id              | Identifier della tupla                                                                                                                                                                               |
| id_master       | Identifier della tupla di formumast a cui fa riferimento la tupla in questione                                                                                                                       |
| fi_inciname     | Nome inci del qq, appare nei qq della formula di un prodotto                                                                                                                                         |
| fi_qtainci      | Qta dell'inci del qq, appare nei qq della formula di un prodotto. La differenza con fi_qtaincicompe é che alcuni inci si modificano post lavorazione. Questo campo fa riferimento al pre lavorazione |
| fi_qtaincicompe | Qta dell'inci del qq, appare nei qq della formula di un prodotto. La differenza con fi_qtainci é che alcuni inci si modificano post lavorazione. Questo campo fa riferimento al post lavorazione     |
| id_prodotto     | Identifier del prodotto a cui questa formula fa riferimento                                                                                                                                          |
| id_prodotto_cmp |                                                                                                                                                                                                      |
| id_inci_master  | Codice dell'Inci a cui l'Inci della tupla attuale viene sommato al fine di soddisfare determinate regole Inci (formumast inciestesa id_master = 603 example)                                         |

-----

### Formumast_inciestesa
La tabella descrive le diverse INCI che compongono la formula QQ del prodotto.

| Attribute       | Meaning                                                                                                                                                                                                                                                                                                                                                                                                   |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id              | Identifier della tupla                                                                                                                                                                                                                                                                                                                                                                                    |
| id_master       | Identifier della tupla di formumast a cui fa riferimento la tupla in questione                                                                                                                                                                                                                                                                                                                            |
| fi_inciname     | Nome inci del qq, appare nei qq della formula di un prodotto                                                                                                                                                                                                                                                                                                                                              |
| fi_qtainci      | Qta dell'inci del qq, appare nei qq della formula di un prodotto. La differenza con fi_qtaincicompe é che alcuni inci si modificano post lavorazione. Questo campo fa riferimento al pre lavorazione. A differenza della tabella precedente, fi_qtainci contiene tutti i dati completi non sommati che fan parte della formula, per ricollegarsi singolarmente ad ogni ingrediente di ogni materia prima. |
| fi_qtaincicompe | Qta dell'inci del qq, appare nei qq della formula di un prodotto. La differenza con fi_qtainci é che alcuni inci si modificano post lavorazione. Questo campo fa riferimento al post lavorazione                                                                                                                                                                                                          |
| id_prodotto     | Identifier del prodotto a cui questa formula fa riferimento                                                                                                                                                                                                                                                                                                                                               |
| id_prodotto_cmp |                                                                                                                                                                                                                                                                                                                                                                                                           |
| id_inci_master  | Codice dell'Inci a cui l'Inci della tupla attuale viene sommato al fine di soddisfare determinate regole Inci (formumast inciestesa id_master = 603 example)                                                                                                                                                                                                                                              |

-----

### Prodotti
Elenco di tutti i prodotti aventi una formula associata.

| Attribute      | Meaning                                                                                                                      |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| id             | Identifier della tupla                                                                                                       |
| codiceext      | Concatenazione di pr_codice e pr_versione                                                                                    |
| pr_codice      | Corrisponde a formumast.fo_codice                                                                                            |
| pr_descri      | Descrizione del prodotto                                                                                                     |
| pr_versione    | Corrisponde a formumast.fo_versione                                                                                          |
| pr_unimis      | Unitá di misura                                                                                                              |
| pr_classe      | Sigle ==??==                                                                                                                 |
| pr_categoria   | 5 diverse voci: semilavorato, materiale confezionamento, materia_prima, **meteria_prima** e prodotto_finito (e spazio vuoto) |
| pr_famiglia    | Macrofamiglia di ogni prodotto (66 risultati non null, 85k tuple vuote)                                                      |
| pr_stato       | ==??==                                                                                                                       |
| pr_rischio     | ==??== (52 diversi valori)                                                                                                   |
| pr_ingrediente | ==??== due diversi valori: 0 e 2                                                                                             |
| pr_formulacode | ==??== simile a pr_codice                                                                                                    |

-----

### Prodotti_cmp
Prodotti composizione ==mi sfugge a cosa serva==

| Attribute        | Meaning                                |
| ---------------- | -------------------------------------- |
| id               | Identifier della tupla                 |
| codiceext        |                                        |
| id_master        | identifier del prodotto di riferimento |
| dd_descri        |                                        |
| dd_numero        |                                        |
| dd_numcas        |                                        |
| dd_posizione     |                                        |
| dd_inciname      |                                        |
| dd_functions     |                                        |
| dd_funzionereale |                                        |

-----

### Formudett
La tabella descrive...

| Attribute     | Meaning                                                      |
| ------------- | ------------------------------------------------------------ |
| id            | Identifier della tupla                                       |
| id_master     | Identifier della formula master proveniente da **formumast** |
| id_componente | Credo faccia riferimento a prodotti                          |
| fd_ordine     | Dettagli dell'ordine della formula, irrilevante              |
| fd_qta        | La quantitá percentuale del componente.                      |
| fd_attivo     | ==??==                                                       |

-----

### Formumast_componenti
La tabella descrive...

| Attribute     | Meaning                                                      |
| ------------- | ------------------------------------------------------------ |
| id            | Identifier della tupla                                       |
| id_master     | Identifier della formula master proveniente da **formumast** |
| id_componente | ==??==                                                       |
| fd_ordine     | Dettagli dell'ordine della formula, irrilevante              |
| fd_qta        | La quantitá percentuale del componente.                      |

-----

# Strutturazione della gerarchia
Ogni prodotto è definito da una formula, composta da materie prime. Alcune di queste materie prime sono definite da formule a loro volta. La struttura risultate è un albero con altezza massima 2.

prodotti -> formumast -> (componenti $\vee$ formudett si completano per i semilavorati. Formudett ha dentro le materie prime dei semilavorati mentre componenti ha i semilavorati) -> formumast_inci -> inciestesa (tutti i dati completi non sommati che fan parte della formula, per ricollegarsi singolarmente ad ogni ingrediente di ogni materia prima).

![[GerarchiaFormule.drawio.png]]

Qual é la differenza tra semilavorato e materia prima?

![[ScreenFormule.png|900]]

La landing page con l'elenco delle formule si presenta cosí. Ogni singola formula, definita da un codice, rimanda ad un'ulteriore pagina che estende ulteriormente le informazioni riguardanti quella stessa formula.

![[ScreenFormulaComponenti.png|1000]]

==formumast_componenti o formudett?==
I dettagli di ogni formula sono estratti da jos_cbl_formumast. Per quanto riguarda i componenti di ogni formula, le componenti sono estratte da jos_cbl_formumast_componenti, facendo un join con jos_cbl_formumast. Il campo id_master in componenti é la chiave esterna che permette il join con id di formumast. In componenti, il campo codiceext contiene la concatenazione tra formumast.fo_codice e il nome del componente.

![[ScreenFormulaMP.png|1000]]

secondo screenshot

Per quanto riguarda le materie prime, spesso e volentieri l'elenco risulta uguale alla formula. Tuttavia, a volte l'elenco differisce per alcune voci in piú (e.g., APC026:2919V:00-KKK.)
==check codice in dataset e controllare id_inci_master==
==?? aggiunta spiegazione differenza==

-----

## Ancorotti
![[CodiceIDProdotti.jpeg]]

A partire dal contenuto di formumast.fo_codice, splitto la stringa seguendo le indicazioni dell'immagine sopra riportata. Questi saranno i valori finali che il modello dovrà essere in grado di predire a partire dalla formula chimica.

La costruzione del dataset si basa sull'iniziale creazione della pivot table a partire da formumast_inciestesa, avente come indice l'id_master e come colonne tutti i possibili nomi inci. Già qui noto delle ripetizioni a causa della tecnica utilizzata per riempire il dataset a monte: i nomi inci sono in realtà una concatenazione del nome inci effettivo e della nomenclatura ctfa utilizzata negli USA. Quindi effettuo un join con prodotti_cmp, per estrarre i nomi inci corretti. Il problema che deriva da questa sostituzione è la presenza di inciname differenti che fanno riferimento allo stesso inci (e.g., **'CHAMOMILLA RECUTITA FLOWER EXTRACT (CHAMOMILLA RECUTITA (MATRICARIA) FLOWER EXTRACT)'** and
 **'CHAMOMILLA RECUTITA FLOWER EXTRACT (Chamomilla Recutita \n(Matricaria) Flower Extract)'** )

-----

## Altre Formule
- Formula con @: formule solo per il regolatorio (diverse rispetto a quelle che sono state prodotte). Sono molto vecchie.
- Formule con BA, VA, SS, GT, LD ecc sono formule di laboratorio, non ancora validate. In genere le prime due lettere sono le iniziali del ricercatore che ha creato la formula, poi c'è il numero di progetto (MF202300093)
- PBABP00749C, pre-bulk, è un semilavorato che poi viene inserito in una formula completa (in questo caso la ABP00749C sarà costituito da PBABP00749C e da un altro semilavorato che in genere si chiama ABPGEL seguito da un numero)
- SFC006004Y-01 sono formule vecchie importate dal vecchio gestionale, uguali alle are me senza i puntini che separano texture, colore, stile

-----

# Data Preprocessing
## Metodologia
## Sbilanciamento dei Dati
I classificatori solitamente assumono che i dati di addestramento siano composti da dati bilanciati e da un costo di misclassificazione uguale, cioè le conseguenze o i costi associati a un particolare tipo di errore nella classificazione sono gli stessi per tutte le classi. In altre parole, il classificatore tratta tutti i tipi di errori (falsi positivi e falsi negativi) come ugualmente costosi\cite{Frasca}.

I classificatori naif tentano di ridurre quantità globali come il tasso di errore, tendendo così a classificare erroneamente gli esempi della classe minoritaria. I rischi di apprendere da un dataset sbilanciato sono per lo più identificati dal fallimento nel generalizzare regole induttive per la classe minoritaria, cioè la difficoltà nell'apprendere su più caratteristiche ma con meno campioni e il fatto che i classificatori ingenui sono spesso orientati verso la classe maggioritaria, e dal rischio di overfitting\cite{Frasca}.

Ma quando un dataset è sbilanciato? Si assuma che i punti siano vettori $x \in \mathbb{R}^n$. È possibile distinguere tra **rarità relativa** e **rarità assoluta**. Con il termine rarità relativa si identificano i casi in cui la classe minoritaria è numericamente inferiore, ma non necessariamente rara, ad esempio, $10^6 \vert 10^3$. In questo caso, la classe minoritaria può essere accuratamente appresa. Con il termine rarità assoluta si identificano i casi in cui la classe minoritaria non è solo numericamente inferiore, ma anche non ben definita, ad esempio, $10^3 \vert 1$.

Si possono ottenere buoni risultati, indipendentemente dalla sproporzione delle classi, se entrambi i gruppi sono ben rappresentati e provengono da distribuzioni non sovrapposte\cite{Johnson}

Il rapporto tra il numero di istanze della classe più frequente e il numero di istanze della classe meno frequente viene chiamato **Rapporto di Sbilanciamento (Imbalance Ratio)**. Per un dataset multiclasse, si possono calcolare i rapporti tra la classe più comune e ciascuna delle altre classi.

### Datasets
#### Datasets per il Modello Decisionale
Il DataFrame in questione, a partire da una formula scelta, é cosí strutturato:

|          | Componente $1$ | ... | Componente $m$ | TOTALE                  |
| -------- | -------------- | --- | -------------- | ----------------------- |
| INCI $1$ | $x_{1,1}$      | ... | $x_{1,m}$      | $\sum_{i=1}^m x_{1, i}$ |
| INCI $2$ | $x_{2,1}$      | ... | $x_{2, m}$     | $\sum_{i=1}^m x_{2, i}$ |
| ...      | ...            | ... | ...            |                         |
| INCI $n$ | $x_{n,1}$      | ... | $x_{n, m}$     | $\sum_{i=1}^m x_{n, i}$ |

dove, nella colonna TOTALE, é contenuta la composizione qualiquantitativa degli INCI della formula in questione.

Per ottere ció, innanzitutto, é necessario creare un primo DataFrame strutturato nel seguente modo:

| Formula | Componente $1$ | ... | Componente $m$ | TOTALE  |
| ------- | -------------- | --- | -------------- | ------- |
|         | $x_{1,1}$      | ... | $x_{1,m}$      | $100\%$ |
|         | $x_{2,1}$      | ... | $x_{2, m}$     | $100\%$ |
| ...     | ...            | ... | ...            | ...     |
|         | $x_{n,1}$      | ... | $x_{n, m}$     | $100\%$ |

Per ottere ció, eseguo un inner join tra _formumast_ e _formumast_componenti_, rimuovendo numerose colonne inutili ai fini di quest'analisi. La tabella _formumast_componenti_ non contiene il corretto nome dei componenti ma un identifier seriale. Di conseguenza, é necessario un ulteriore join tra la tabella ottenuta precedentemente e _prodotti_. Al risultato di questo merge viene applicato un pivot: la colonna _fo_codice_ viene utilizzata come indice del nuovo DataFrame. Le colonne del nuovo DF sono tutti i valori della colonna _pr_codice_, ovvero i nomi dei componenti. Il valore contenuto nelle celle é preso da _fs_qta_, aggregato tramite la funzione _first_ solo la prima occorrenza della coppia $\langle fo\_codice, pr\_codice \rangle$). 

![[Tabella1.png]]

Ora necessito di un DataFrame contenente ogni diversa componente e la scomposizione in INCI di tale componente. Le componenti di ogni prodotto sono contenute in _prodotti_cmp_, dove il campo di interesse é _dd_percpart_. 

![[Prodotti_Cmp.PNG]]

Tramite un inner join con _prodotti_, estraggo sia il codice sia la categoria di tale prodotto.

immagine tmp3 pd merge tmp2 prodotti

Creo una lista contenente tutti i metalli pesanti e li rimuovo, in quanto la loro percentuale di presenza é giá sommata agli altri INCI. Tenerli significherebbe avere un totale superiore al 100%

==la domanda ora é se, al fine di costruire la tabella desiderata, io debba considerare tutte le categorie (materia prima o semilavorato) o solo semilavorato.

Mi aspettavo inoltre che la percpart delle materie prime fosse sempre $100\%$, ma non é cosí. 


| Codice Formula        | *ABA009 BASE_0 | *AGA011 BASE NEW_0 | ... | nan_0 | total |
| --------------------- | -------------- | ------------------ | --- | ----- | ----- |
| BASE IMPACT           | 0.0            | 0.0                | ... | 0.0   | 100.0 |
| EG/CA202100135:01B:10 | 0.0            | 0.0                | ... | 0.0   | 100.0 |
| **ABA00907V           | 96.5           | 0.0                | ... | 0.0   | 100.0 |
| **ARA018312C          | 0.0            | 0.0                | ... | 0.0   | 100.0 |
| *ABA009 BASE          | 0.0            | 0.0                | ... | 0.0   | 100.0 |
| ...                   | ...            | ...                | ... | ...   | ...   |
| AGA01914V-02          | 0.0            | 0.0                | ... | 0.0   | 100.0 |
| AGA019150R            | 0.0            | 0.0                | ... | 0.0   | 100.0 |
| AGA019151P            | 0.0            | 0.0                | ... | 0.0   | 100.0 |

Partendo dal DataFrame contenente le formule dei prodotti cosmetici, viene selezionata una formula.

|                | Componente $1$ | Componente $2$ | ... | Componente $n$ | Totale |
| -------------- | -------------- | -------------- | --- | -------------- | ------ |
| Codice Formula | $v_1$          | $v_2$          | ... | $v_n$          | 100.0  |

E.g., "\*ABA009 BASE":

|              | B000016_0 | B000107_0 | B0001501_0 | B000291_0 | B100404_0 | E0001389_0 | total |
| ------------ | --------- | --------- | ---------- | --------- | --------- | ---------- | ----- |
| *ABA009 BASE | 2.0       | 17.4      | 10.0       | 13.1      | 57.4      | 0.1        | 100.0 |

Da questo DataFrame, si estraggono due liste:
- una lista contenente il nome delle componenti presenti nella formula;
- una lista contenente le percentuali di queste componenti.

Ad ogni componente della formula scelta viene sostituita la composizione qualiquantitative

|            | 1,2-HEXANEDIOL | 2-METHYL 5-CYCLOHEXYLPENTANOL | ... | Zingiber Officinale Oil | total Formula |
| ---------- | -------------- | ----------------------------- | --- | ----------------------- | ------------- |
| B000016_0  | 0.0            | 0.0                           | ... | 0.0                     | 100.0         |
| B000107_0  | 0.0            | 0.0                           | ... | 0.0                     | 100.0         |
| B0001501_0 | 0.0            | 0.0                           | ... | 0.0                     | 100.0         |
| B000291_0  | 0.0            | 0.0                           | ... | 0.0                     | 100.0         |
| B100404_0  | 0.0            | 0.0                           | ... | 0.0                     | 100.0         |
| E0001389_0 | 0.0            | 0.0                           | ... | 0.0                     | 100.0         |

Dopo aver trasposto il DataFrame per avere le materie prime sulle righe invece che sulle colonne, viene scalato ogni componente in base alla sua percentuale presente nella formula. Inoltre, viene eseguita la somma dei valori su ciascuna riga. Il risultato viene assegnato ad una nuova colonna chiamata _total QQ_.

| INCI                          | B000016_0 | B000107_0 | B0001501_0 | B000291_0 | B100404_0 | E0001389_0 | total QQ |
| ----------------------------- | --------- | --------- | ---------- | --------- | --------- | ---------- | -------- |
| 1,2-HEXANEDIOL                | 0.0       | 0.0       | 0.0        | 0.0       | 0.0       | 0.0        | 0.0      |
| 2-METHYL 5-CYCLOHEXYLPENTANOL | 0.0       | 0.0       | 0.0        | 0.0       | 0.0       | 0.0        | 0.0      |
| ...                           | ...       | ...       | ...        | ...       | ...       | ...        | ...      |
| ZINGIBER OFFICINALE ROOT OIL  | 0.0       | 0.0       | 0.0        | 0.0       | 0.0       | 0.0        | 0.0      |
| Zingiber Officinale Oil       | 0.0       | 0.0       | 0.0        | 0.0       | 0.0       | 0.0        | 0.0      |
| total Formula                 | 2.0       | 17.4      | 10.0       | 13.1      | 57.4      | 0.1        | 100.0    |


-----