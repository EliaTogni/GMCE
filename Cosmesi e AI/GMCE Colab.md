# GMCE
Lo scopo di questa pagina COLAB é di provare a trovare delle similaritá nelle formule, al fine di validare poi le soluzioni fornite dal modello di ottimizzazione tramite questi risultati.

Il codice accede a Google Drive al fine di poter accedere ai dataset di interesse in maniera comoda da diverse macchine. Il primo step é, infatti, l'import di tutti i CSV ottenuti precedentemente tramite query SQL sul DBMS aziendale.

Questo primo sheet di Google Colab ha lo scopo iniziale di permettere una iniziale panoramica dei dati contenuti nei vari file CSV e cercare di carpire eventuali relazioni (lineari e non) e pattern esistenti tra i dati.

Il lavoro ruota attorno a modelli di apprendimento automatico. Il mio primo obiettivo è più uno "studio di fattibilità" tramite modelli più semplici. Invece di utilizzare tutte le colonne di output, ne uso inizialmente un sottoset. Devo quindi decidere quali output scegliere: se la famiglia dei prodotti (prodotti["pr_famiglia"] con 66 classi), il tipo di prodotto (seconda lettera di formumast["fo_codice"] con 15 classi) oppure la classe dei prodotti (prodotti["pr_classe"] con 25 classi). Ho optato per formumast["fo_codice"] grazie a insights fornitimi da ...

I DataFrame da me realizzati in quanto ritenuti di mio futuro interesse sono:

- Un DF contenente una tupla per ogni formula. Ogni tupla rappresenta la composizione QQ della formula. Nessuna colonna viene considerata come di output in quanto questo DataFrame verrà utilizzato per un training di un modello di unsupervised learning (clustering);
- Un DF contenente una tupla per ogni formula. Ogni tupla rappresenta la composizione QQ della formula. Una singola colonna viene considerata come di output in quanto contiene il tipo di prodotto (estratto dalla seconda lettera di fo_codice). Ci sono in tutto 15 tipi di prodotti possibili nella tabella. Questo DataFrame verrà utilizzato per un training di un modello di learning supervised (MLNN con diverse architetture).

La generazione di questi DataFrame ha numerosi step in comune, per poi differenziarsi negli ultimi passaggi.

Le differenze in termini di cardinalità tra formumast_inci e formumast_inciestesa è dovuta a
- datasets non aggiornato backend side;
- metalli in formumast_inci e non in formumast_inciestesa.
Post aggiornamento dei dataset, la differenza di elementi unici si è ridotta a solo 11 elementi.

In termini di tuple, invece, la differenza è di 461012 elementi. Questo è dovuto alla presenza dei metalli pesanti nella tabella formumast_inci. Nella tabella formumast_inciestesa, questi metalli sono già conteggiati negli altri ingredienti.

In formumast_inciestesa è contenuto il nome INCI concatenato al nome CTFA. Quindi, estraggo tutti i nomi INCI corretti dalla tabella prodotti_cmp. Poi, tramite un inner join tra prodotti_cmp_tmp e formumast_inciestesa, recupero sia gli inciname corretti che quelli errati. Controllo anche che inciname (INCI + CTFA) differenti di poco, tipicamente per spazi o termini in lowercase, siano associati allo stesso nome INCI.

Per trovare tutte le tuple nel DataFrame "inciestesa_final" aventi lo stesso valore di "dd_inciname" ma valori diversi di "fi_inciname", é necessario:
- gruppare per dd_inciname e contare i valori unici di fi_inciname;
- filtrare i gruppi aventi più di un valore unico di fi_inciname;
- utilizzare questi gruppi per filtrare il DataFrame originale.

Procedo quindi all'eliminazione delle feature che ho ritenuto irrilevanti ai fini della task di classificazione. Ho mantenuto solamente gli identifiers (i quali mi serviranno più avanti), i nomi INCI (che utilizzerò come nomi delle colonne della tabella pivot) e fi_qtainci. 

#che fi_qtaincicompe. Nell'analisi, inizialmente, proverò ad utilizzare fi_qtainci. fi_qtaincicompe contiene le #quantità degli INCI dopo la lavorazione, ovvero ciò che va sull'etichetta del prodotto. Le due formule QQ #differiscono di poco ma ci sono delle regole nella scrittura dell'etichetta che andranno considerate #(id_inci_master).

Creo poi la tabella pivot avente come features i diversi nomi INCI corretti ed i corrispettivi valori. Sostituisco inoltre i valori NaN (ogniqualvolta un INCI non compare nella formula di un prodotto) con il valore 0. Come funzione di aggregazione ho scelto di utilizzare la somma nel caso compaia lo stesso INCI più volte per una formula. Tecnicamente non dovrebbe succedere ma in fase di testing ho notato che ci sono delle eccezioni.

Estraggo solamente i codici da formumast["fo_codice"] dei quali la composizione ha un significato in termini strutturali.

Continuo l'operazione di estrazione, ottenendo circa 66k prodotti (#di Ancorotti). Purtroppo il campo fo_descri, il quale contiene delle descrizioni piú o meno dettagliate sul risultato ottenibile dalla formula, è troppo disomogeneo per essere utilizzato.

A questo punto, rimuovo tutte le features non di mio interesse: fo_texture, fo_colore e fo_stile sono tutte ricavabili da fo_codice (in quanto non é altro che una concatenazione delle precedenti features). Le altre features del dataset non sono state ritenute utili ai fini dell'analisi.

Ora eseguo un inner join tra i due DataFrame ottenuti e controllo anche che non ci siano delle colonne duplicate per sbaglio.

Il primo degli step successivi è assicurarsi che tutti i codici contenuti in fo_codice siano conformi alla struttura attesa. Cosa che non succede, come si può osservare dal risultato: ci sono migliaia di codici di lunghezza diversa:
- codici che finiscono con una o più K;
- codici lunghi meno di 3 caratteri o più di 20;

==spiegazione==

Definisco quindi una funzione per controllare che il contenuto sia valido, ovvero che il totale della composizione QQ degli INCI raggiunga il 100%. Ho prima testato questa funzione su un sottoset di prova, per via delle ridotte dimensioni.

===paragrafo ulteriore di spiegazione del codice===

La cifra mi ha insospettito ma il totale fa davvero 113.86 anche dal software. Quindi creo un dizionario per tutti gli fo_codici e scarto quelli il cui totale sia diverso da 100% + \varepsilon. 

#Il tutto ci mette circa 5 minuti ed é il collo di bottiglia del processo dal punto di vista della RAM.
Ci sono circa 10k codici duplicati.

Ora rimuovo tutte le tuple in cui il secondo carattere di fo_codice (identificativo del tipo di prodotto) non corrisponde ad alcun tipo di prodotto conosciuto. Inoltre, proseguendo con gli step, ho notato che probabilmente il numero di caratteri in seconda posizione in fo_codice è maggiore di quelli previsti dalla struttura delle formule di Ancorotti. Allora ho aggiunto questo blocco di codice che esclude le tuple errate. Questa fase di preprocessing sta inevitabilmente sfoltendo molto il dataset.

Infatti dovrebbero essere 15 ma sono 18. Non benissimo pt. 2. H, 3, e c non dovrebbero esistere.

## Modelli

Si tratta di un problema di classificazione in quanto le colonne di output rappresentano delle classi da classificare.

#Il problema ora riguarda quale tecnica scegliere e come gestire la grande sparsità del dataset. Ho due macroidee: #la prima è di provare una tecnica unsupervised e vedere quanto la sparsità del dataset influisca sulla previsione #mentre la seconda comporta il considerare il tipo di prodotto estraendo la seconda lettera da "fo_codice".


Provo a plottare inizialmente come sono fatti i cluster

immagine 1 e 2

Alcuni cluster (come il 2 e il 7) appaiono molto distinti e separati, mentre altri cluster (come il 3 e il 5) sono più vicini e potenzialmente sovrapposti, suggerendo che i dati in queste aree potrebbero avere caratteristiche simili e non essere facilmente separabili. Altri cluster, come l'11 (viola chiaro) e il 10 (grigio), sono più diffusi, indicando una maggiore variabilità all'interno del cluster.

Prima Componente (PCA1): Probabilmente cattura la maggior parte della varianza nei dati, con cluster distesi lungo questa direzione


Alcuni cluster (es. cluster 1) contengono una gran parte dei campioni, indicando uno sbilanciamento. Questo potrebbe significare che il modello di clustering sta sovra-aggregando alcuni dati. Nel cluster 1, c'è una confusione significativa tra molte classi reali, indicando che il clustering non sta separando bene le classi.
Diversi cluster hanno pochissimi campioni, il che potrebbe significare che non sono utili nella rappresentazione di alcuna classe.
Potrebbe essere utile rivedere il numero di cluster utilizzato. Forse un diverso valore di num_clusters potrebbe migliorare la separazione tra le classi.
o
Per valutare la bontà dei clusters posso usare differenti metriche (descritte su overleaf come il jaccard index)

-----

# GMCEModelloDecisionale

-----

# GMCEGurobi


-----

# GMCEGurobiTest


-----

# GMCEGurobiTest1


-----

# GMCEGurobiTest2


-----

# ModificaComponenti


-----