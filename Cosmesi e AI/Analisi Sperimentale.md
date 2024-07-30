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

-----

L'utilizzo del modello di clustering ha lo scopo di osservare se formule che descrivono prodotti della stessa categoria sono vicine nello spazio chimico. Se questa proprietá dovesse essere verificata, sarebbe una prima conferma della validitá del risultato ottenuto tramite il modello decisionale.

Il clustering é stato quindi effettuato scegliendo 12 come numero di cluster in quanto il campo ... contiene 12 diverse famiglie di prodotti. Ogni punto nello spazio $n$-dimensionale rappresenta la composizione qualiquantitativa di una data formula.

![[clusters.png]]