# Modello Decisionale
## Modello 1
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
A partire da una tabella strutturata come quella soprastante, si sceglie una colonna contenente una componente. Questa componente viene "blacklistato", cioé non puó piú essere utilizzato nella formula. Il ruolo del modello é trovare il minor numero di altre componenti che permettano di avere una composizione QQ il piú vicino possibile a quella originale. La metrica di distanza utilizzata per valutare la vicinanza tra composizioni qualiquantitative é la distanza Euclidea.

Si indicizzano con $i$ gli INCI (sulle righe) e con $j$ le componenti (sulle colonne).

-------
## DATI
**param nINCI** \#numero di INCI presenti nel modello
**set I {nINCI}** \#set di tutti gli INCI
**param nComponenti** \#numero di componenti presenti nel modello (tranne quello blacklistato)
**set Componenti {nComponenti}** \#set di tutti i componenti
**param percentuale** \#percentuale della formula da sostituire
**set Totale {nINCI}** \#composizione QQ finale

----------
## VARIABILI
**var x {nComponenti} float** \#percentuale di ciascuna componente  
**var y {nComponenti} binary** #1 se la componente viene scelta, 0 altrimenti

------
## VINCOLI
$$\sum_j x_j = percentuale$$
$$x_j \leq q_j\cdot y_j$$

  1) voglio far sí che le altre componenti non blacklistate possano essere aumentate in termini di percentuale? (aka faccio sí che si possano scegliere tra le componenti da aggiungere ma, nel caso, la funzione da minimizzare va riscritta in qualche modo)
  2) Come definiamo $\varepsilon$?

------

## OBIETTIVO

 $minimize \sum_J y_j$  \#minimizzare il numero di componenti scelte

-----

Apportiamo alcune modifiche. Innanzitutto, la somma degli INCI di tutte le componenti utilizzate non deve superare quella nella formula QQ.

$$\sum_J a_{ij}\cdot x_j \leq b_i + \varepsilon$$
$$a_{ij} \cdot x_{j} \leq b_i + \varepsilon \space \forall i, \forall j$$
$$\forall j \space \max_i a_{ij} \cdot x_j - b_i - \varepsilon \leq 0$$
$$x_j \leq \frac{b_i + \varepsilon}{a_{ij}} \space \forall i$$
$$x_j \leq \min_{i} \frac{b_i + \varepsilon}{a_j}$$
$$ \text{calcolo tramite preprocessing } q_j = \min_{i} \frac{b_i + \varepsilon}{a_{ij}}$$
$$x_j \leq q_j \cdot y_j \text{ con } y_j \text{ variabile binaria}$$
-----

\#minimizzare la vicinanza tra la composizione INCI iniziale e quella post sostituzione

-----

# Modello di Clustering


-----

# Multi Layer Neural Network Model


-----