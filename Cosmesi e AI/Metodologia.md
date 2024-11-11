# Workflow

Comparazione tra workflow del formulatore e del software

-----

# Struttura del software

figma -> mock del software

-----

# Modulo del preprocessing

-----

# Modelli

## Modello Decisionale
### Modello 1
```pseudo
	\begin{algorithm}
	\caption{Decisional Model}
	\begin{algorithmic}
		\State minimize $\sum_{j = 1}^{\vert \mathcal{J} \vert} y_j$
		\State s.t. $\sum_{j \in \mathcal{J}} a_{i, j} x_j \leq b_i + \varepsilon$,
		\State s.t. $\sum_{j \in \mathcal{J}} a_{i, j} x_j \geq b_i - \varepsilon$,
		\State s.t. $x_j \leq y_j$
	\end{algorithmic}
	\end{algorithm}
```

|          | $y_1$          | ... | $y_{nComponenti}$ |                         |
| -------- | -------------- | --- | ----------------- | ----------------------- |
|          | Componente $1$ | ... | Componente $m$    | Totale                  |
| INCI $1$ | $x_{1,1}$      | ... | $x_{1,m}$         | $\sum_{i=1}^m x_{1, i}$ |
| INCI $2$ | $x_{2,1}$      | ... | $x_{2, m}$        | $\sum_{i=1}^m x_{2, i}$ |
| ...      | ...            | ... | ...               |                         |
| INCI $n$ | $x_{n,1}$      | ... | $x_{n, m}$        | $\sum_{i=1}^m x_{n, i}$ |

A partire da una formula precedentemente selezionata e scomposta nel DataFrame _transposed_normalized_, si sceglie una colonna facente riferimento ad una componente. Questa componente viene "blacklistata", cioé non puó piú essere utilizzata all'interno della formula. L'obiettivo del modello é trovare il minor numero di altre componenti che permettano di avere una composizione QQ il piú vicino possibile a quella originale. La metrica di distanza utilizzata per valutare la vicinanza tra composizioni qualiquantitative é la distanza Euclidea.

Il procedimento é il seguente:

- si memorizza la composizione QQ degli INCI;
- scelta la colonna da rimuovere, si memorizza la percentuale della componente corrispondente presente nella riga _total Formula_;
- si rimuove da _Tabella_Componenti_ la componente blacklistata (per far sì che non venga scelta nuovamente dal modello di ottimizzazione);
- il modello sceglie le componenti da _Tabella_Componenti_, le quali andranno a sostituire la componente rimossa.

Si indicizzano con $i$ gli INCI (sulle righe) e con $j$ le componenti (sulle colonne).

-------
### DATI
**param nINCI** \#numero di INCI presenti nel modello
**set I {nINCI}** \#set di tutti gli INCI
**param nComponenti** \#numero di componenti presenti nel modello (tranne quello blacklistato)
**set Componenti {nComponenti}** \#set di tutti i componenti
**param percentuale** \#percentuale della formula da sostituire
**set Totale {nINCI}** \#composizione QQ finale

----------
### VARIABILI
**var x {nComponenti} float** \#percentuale di ciascuna componente  
**var y {nComponenti} binary** #1 se la componente viene scelta, 0 altrimenti

------
### VINCOLI

$$\sum_J a_{ij}\cdot x_j \leq b_i + \varepsilon \space \forall i$$
$$\sum_J a_{ij}\cdot x_j \geq b_i - \varepsilon \space \forall i$$
$$x_j \leq y_j$$


------


### OBIETTIVO

 $minimize \sum_J y_j$  \#minimizzare il numero di componenti scelte

-----

Il modello é in grado di aumentare la percentuale delle altre componenti non blacklistate per compensare l'assenza della componente rimossa. Questa feature é stata ottenuta semplicemente mantenendo all'interno del DataFrame delle componenti quelle giá presenti nella formula.

Il valore $\varepsilon$


-----

### Modello 2

Apportiamo alcune modifiche. Innanzitutto, la somma degli INCI di tutte le componenti utilizzate non deve superare quella nella formula QQ.

$$\sum_J a_{ij}\cdot x_j \leq b_i + \varepsilon$$
$$a_{ij} \cdot x_{j} \leq b_i + \varepsilon \space \forall i, \forall j$$
$$\forall j \space \max_i a_{ij} \cdot x_j - b_i - \varepsilon \leq 0$$
$$x_j \leq \frac{b_i + \varepsilon}{a_{ij}} \space \forall i$$
$$x_j \leq \min_{i} \frac{b_i + \varepsilon}{a_j}$$
$$ \text{calcolo tramite preprocessing } q_j = \min_{i} \frac{b_i + \varepsilon}{a_{ij}}$$

In questo modo, il vincolo 

$$x_j \leq y_j$$

viene modificato in 

$$x_j \leq q_j \cdot y_j$$

-----


-----

## Modello Decisionale 2

Prendere una formula, togliere tutte le componenti tenendo la composizione qualiquantitativa e richiedere al modello di scegliere tot ingredienti in quantità variabili al fine di ottenere una qq finale vicina a quella fornita.


-----

## Modello di Clustering


-----

## Modello di Multi Layer Neural Network


-----