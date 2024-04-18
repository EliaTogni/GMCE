
| Tabella                          | Collegata con                | Join            | Collegamento                                                                |
| -------------------------------- | ---------------------------- | --------------- | --------------------------------------------------------------------------- |
| jos_cbl_bldett                   | jos_cbl_blmast               | INNER JOIN      | jos_cbl_bldett.id_master=jos_cbl_blmast.id                                  |
| jos_cbl_formumast                | jos_cbl_prodotti             | INNER JOIN      | jos_cbl_formumast.id_prodotto=jos_cbl_prodotti.id                           |
| jos_cbl_formudett                | jos_cbl_formumast            | INNER JOIN      | jos_cbl_formudett.id_master=jos_cbl_formumast.id                            |
| jos_cbl_formudett                | jos_cbl_prodotti             | INNER JOIN      | jos_cbl_formudett.id_componente=jos_cbl_prodotti.id                         |
| jos_cbl_formumast_inciestesa     | jos_cbl_formumast            | INNER JOIN      | jos_cbl_formumast_inciestesa.id_master=jos_cbl_formumast.id                 |
| jos_cbl_formumast_inciestesa     | jos_cbl_prodotti             | INNER JOIN      | jos_cbl_formumast_inciestesa.id_prodotto=jos_cbl_prodotti.id                |
| jos_cbl_formumast_inciestesa     | jos_cbl_prodotti_cmp         | INNER JOIN      | jos_cbl_formumast_inciestesa.id_prodotto_cmp=jos_cbl_prodotti_cmp.id        |
| jos_cbl_formumast_inciestesa     | jos_cbl_formumast_inciestesa | LEFT OUTER JOIN | jos_cbl_formumast_inciestesa.id=jos_cbl_formumast_inciestesa.id_inci_master |
| jos_cbl_formumast_inci           | jos_cbl_formumast            | INNER JOIN      | jos_cbl_formumast_inci.id_master=jos_cbl_formumast.id                       |
| jos_cbl_formumast_inci           | jos_cbl_prodotti             | LEFT OUTER JOIN | jos_cbl_formumast_inci.id_prodotto=jos_cbl_prodotti.id                      |
| jos_cbl_formumast_inci           | jos_cbl_prodotti_cmp         | LEFT OUTER JOIN | jos_cbl_formumast_inci.id_prodotto_cmp=jos_cbl_prodotti_cmp.id              |
| jos_cbl_formumast_inci           | jos_cbl_formumast_inci       | LEFT OUTER JOIN | jos_cbl_formumast_inci.id_inci_master=jos_cbl_formumast_inci.id             |
| jos_cbl_formumast_trasformazioni | jos_cbl_formumast            | INNER JOIN      | jos_cbl_formumast_trasformazioni.id_master=jos_cbl_formumast.id             |
| jos_cbl_prodotti_cmp             | jos_cbl_prodotti             | INNER JOIN      | jos_cbl_prodotti_cmp.id_master=jos_cbl_prodotti.id                          |