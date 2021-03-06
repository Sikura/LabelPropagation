Label Propagation
============================================
<p align="justify">
Label Propagation is a randomized community detection algorithm, it gives a large number of small sized clusters. It is a useful benchmark.  
</p>

This repository provides a reference implementation for Label Propagation.

### Requirements

The codebase is implemented in Python 2.7. package versions used for development are just below.
```
networkx          1.11
tqdm              4.19.5
numpy             1.13.3
pandas            0.20.3
jsonschema        2.6.0
```

### Datasets

The code takes an input graph in a csv file. Every row indicates an edge between two nodes separated by a comma. The first row is a header. Nodes should be indexed starting with 0. Sample graphs for the `Facebook Politicians` dataset is included in the  `data/` directory.

### Options

Creating a clustering is handled by the `src/label_propagation.py` script which provides the following command line arguments.

#### Model options

```
  --input STR                Input graph path.                          Default is `data/politician_edges.csv`.                                     
  --assignment-output STR    Node-cluster assignment dictionary path.   Default is `output/politician.json`.
  --weighing STR             Weighting strategy.                        Default is `overlap`.
  --rounds INT               Number of iteations.                       Default is 30.
  --seed INT                 Initial seed           .                   Default is 42.
```

### Examples

The following commands create cluster assignments and writes them to disk.

Creating communities for the default dataset with the default hyperparameter settings.

```
python src/label_propagation.py
```
Using unit weighted label propagation.

```
python src/label_propagation.py --weighting unit
```

Changing the random seed.

```
python src/label_propagation.py --seed 32
```

Using label propagation with 100 iteration rounds.

```
python src/embedding_clustering.py --rounds 100
```
