
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

## Primo ER

![[ERCosmesi.drawio.png |]]

-----

## Secondo ER


# Tabelle

## Formumast
La tabella descrive

| Attribute      | Meaning                                                                                                                                                                          |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id             | Identifier della tupla                                                                                                                                                           |
| fo_codice      | codice indicativo della formula. Appare nella pagina dei qq nel campo **Codice**. E' ottenuto (non sempre purtroppo) tramite concatenazione di fo_texture, fo_colore e fo_stile. |
| fo_descri      | Stringa che descrive il prodotto ottenuto dalla formula (==descrizione inconsistente==). Appare nella pagina dei qq nel campo **Descrizione**.                                   |
| id_prodotto    | Appare nella pagina dei qq nel campo **Prodotto**. E' ottenuto (non sempre purtroppo) tramite concatenazione di codice e descrizione.                                            |
| codiceext      | ==mi sfugge il significato==                                                                                                                                                     |
| codazie        | Questo campo ha sempre valore **More**.                                                                                                                                          |
| fo_versione    | Intero che indica la versione della formula. Appare nella pagina dei qq nel campo **Descrizione**.                                                                               |
| fo_stato       | Stringa che indica lo stato della formula. Può essere **In revisione**, **Approvato**, **Obsoleto**. Appare nella pagina dei qq nel campo **Stato**.                             |
| fo_unimis      | G, g, NAN, kg                                                                                                                                                                    |
| fo_texture     | Appare nella pagina dei qq nel campo **Texture**.                                                                                                                                |
| fo_colore      | Appare nella pagina dei qq nel campo **Colore**.                                                                                                                                 |
| fo_stile       | Appare nella pagina dei qq nel campo **Stile**.                                                                                                                                  |
| id_formorigine |                                                                                                                                                                                  |

-----

## Formumast_inci

| Attribute       | Meaning                                                                        |
| --------------- | ------------------------------------------------------------------------------ |
| id              | Identifier della tupla                                                         |
| id_master       | Identifier della tupla di formumast a cui fa riferimento la tupla in questione |
| fi_inciname     | Nome inci del qq, appare nei qq della formula di un prodotto                   |
| fi_qtainci      |                                                                                |
| fi_qtaincicompe | Qta dell'inci del qq, appare nei qq della formula di un prodotto               |
| id_prodotto     |                                                                                |
| id_prodotto_cmp |                                                                                |
| id_inci_master  | ==sono tutti zero, non capisco a cosa serva==                                  |

-----

## Formumast_inciestesa

| Attribute       | Meaning                                                                        |
| --------------- | ------------------------------------------------------------------------------ |
| id              | Identifier della tupla                                                         |
| id_master       | Identifier della tupla di formumast a cui fa riferimento la tupla in questione |
| fi_inciname     | Nome inci del qq, appare nei qq della formula di un prodotto                   |
| fi_qtainci      |                                                                                |
| fi_qtaincicompe | Qta dell'inci del qq, appare nei qq della formula di un prodotto               |
| id_prodotto     |                                                                                |
| id_prodotto_cmp |                                                                                |
| id_inci_master  | ==sono tutti zero, non capisco a cosa serva==                                  |

Check via colab per differenze con formumast_inci

-----

## Prodotti

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

## Prodotti_cmp

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

## Formudett
La tabella descrive...

| Attribute | Meaning                                                      |
| --------- | ------------------------------------------------------------ |
| id        | Identifier della tupla                                       |
| id_master | Identifier della formula master proveniente da **formumast** |
| fd_ordine | Dettagli dell'ordine della formula                           |

-----

Screen 192.168.223.35/formuleAI/

