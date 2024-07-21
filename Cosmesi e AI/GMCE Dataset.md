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


![[ERCosmesi.drawio.png |]]

-----

# Tabelle
### Formumast
La tabella descrive

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

| Attribute       | Meaning                                                                                                                                                      |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id              | Identifier della tupla                                                                                                                                       |
| id_master       | Identifier della tupla di formumast a cui fa riferimento la tupla in questione                                                                               |
| fi_inciname     | Nome inci del qq, appare nei qq della formula di un prodotto                                                                                                 |
| fi_qtainci      |                                                                                                                                                              |
| fi_qtaincicompe | Qta dell'inci del qq, appare nei qq della formula di un prodotto                                                                                             |
| id_prodotto     |                                                                                                                                                              |
| id_prodotto_cmp |                                                                                                                                                              |
| id_inci_master  | Codice dell'Inci a cui l'Inci della tupla attuale viene sommato al fine di soddisfare determinate regole Inci (formumast inciestesa id_master = 603 example) |

-----

### Formumast_inciestesa

| Attribute       | Meaning                                                                                                                                                      |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id              | Identifier della tupla                                                                                                                                       |
| id_master       | Identifier della tupla di formumast a cui fa riferimento la tupla in questione                                                                               |
| fi_inciname     | Nome inci del qq, appare nei qq della formula di un prodotto                                                                                                 |
| fi_qtainci      |                                                                                                                                                              |
| fi_qtaincicompe | Qta dell'inci del qq, appare nei qq della formula di un prodotto                                                                                             |
| id_prodotto     |                                                                                                                                                              |
| id_prodotto_cmp |                                                                                                                                                              |
| id_inci_master  | Codice dell'Inci a cui l'Inci della tupla attuale viene sommato al fine di soddisfare determinate regole Inci (formumast inciestesa id_master = 603 example) |

Check via colab per differenze con formumast_inci

-----

### Prodotti

| Attribute      | Meaning                |
| -------------- | ---------------------- |
| id             | Identifier della tupla |
| codiceext      |                        |
| pr_codice      |                        |
| pr_descri      |                        |
| pr_versione    |                        |
| pr_unimis      |                        |
| pr_classe      |                        |
| pr_categoria   |                        |
| pr_famiglia    |                        |
| pr_stato       |                        |
| pr_rischio     |                        |
| pr_ingrediente |                        |
| pr_formulacode |                        |

-----

### Prodotti_cmp

| Attribute        | Meaning                |
| ---------------- | ---------------------- |
| id               | Identifier della tupla |
| codiceext        |                        |
| id_master        |                        |
| dd_descri        |                        |
| dd_numero        |                        |
| dd_numcas        |                        |
| dd_posizione     |                        |
| dd_inciname      |                        |
| dd_functions     |                        |
| dd_funzionereale |                        |


-----

### Formudett
La tabella descrive...

| Attribute | Meaning                                                      |
| --------- | ------------------------------------------------------------ |
| id        | Identifier della tupla                                       |
| id_master | Identifier della formula master proveniente da **formumast** |
| fd_ordine | Dettagli dell'ordine della formula                           |

-----

Screen 192.168.223.35/formuleAI/


-----

# Strutturazione della gerarchia

Ogni prodotto è definito da una formula, composta da materie prime. Alcune di queste matere prime sono definite da formule a loro volta. La struttura risultate è un albero che dovrebbe avere altezza massima $2$ ma non ho ancora esplorato i dati.

prodotti -> formumast -> (componenti $\vee$ formudett si completano per i semilavorati. Formudett ha dentro le materie prime dei semilavorati mentre componenti ha i semilavorati) -> formumast_inci -> inciestesa (tutti i dati completi non sommati che fan parte della formula, per ricollegarsi singolarmente ad ogni ingrediente di ogni materia prima)

immagine gerarchia tramite draw.io

-----

## Ancorotti

![[CodiceIDProdotti.jpeg]]

A partire dal contenuto di formumast.fo_codice, splitto la stringa seguendo le indicazioni dell'immagine sopra riportata.
Questi saranno i valori finali che il modello dovrà essere in grado di predire a partire dalla formula chimica.

La costruzione del dataset si basa sull'iniziale creazione della pivot table a partire da formumast_inciestesa, avente come indice l'id_master e come colonne tutti i possibili nomi inci. Già qui noto delle ripetizioni a causa della tecnica utilizzata per riempire il dataset a monte: i nomi inci sono in realtà una concatenazione del nome inci effettivo e della nomenclatura ctfa utilizzata negli USA. Quindi effettuo un join con prodotti_cmp, per estrarre i nomi inci corretti. Il problema che deriva da questa sostituzione è la presenza di inciname differenti che fanno riferimento allo stesso inci (e.g., **'CHAMOMILLA RECUTITA FLOWER EXTRACT (CHAMOMILLA RECUTITA (MATRICARIA) FLOWER EXTRACT)'** and
 **'CHAMOMILLA RECUTITA FLOWER EXTRACT (Chamomilla Recutita \n(Matricaria) Flower Extract)'** )

# Data Preprocessing
## Metodologia

## Sbilanciamento dei Dati
I classificatori solitamente assumono che i dati di addestramento siano composti da dati bilanciati e da un costo di misclassificazione uguale, cioè le conseguenze o i costi associati a un particolare tipo di errore nella classificazione sono gli stessi per tutte le classi. In altre parole, il classificatore tratta tutti i tipi di errori (falsi positivi e falsi negativi) come ugualmente costosi\cite{Frasca}.

I classificatori naif tentano di ridurre quantità globali come il tasso di errore, tendendo così a classificare erroneamente gli esempi della classe minoritaria. I rischi di apprendere da un dataset sbilanciato sono per lo più identificati dal fallimento nel generalizzare regole induttive per la classe minoritaria, cioè la difficoltà nell'apprendere su più caratteristiche ma con meno campioni e il fatto che i classificatori ingenui sono spesso orientati verso la classe maggioritaria, e dal rischio di overfitting\cite{Frasca}.

Ma quando un dataset è sbilanciato? Si assuma che i punti siano vettori $x \in \mathbb{R}^n$. È possibile distinguere tra **rarità relativa** e **rarità assoluta**. Con il termine rarità relativa si identificano i casi in cui la classe minoritaria è numericamente inferiore, ma non necessariamente rara, ad esempio, $10^6 \vert 10^3$. In questo caso, la classe minoritaria può essere accuratamente appresa. Con il termine rarità assoluta si identificano i casi in cui la classe minoritaria non è solo numericamente inferiore, ma anche non ben definita, ad esempio, $10^3 \vert 1$.

euristica sbilanciamento multiclasse

Si possono ottenere buoni risultati, indipendentemente dalla sproporzione delle classi, se entrambi i gruppi sono ben rappresentati e provengono da distribuzioni non sovrapposte\cite{Johnson}