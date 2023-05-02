# DLemb

DLemb is an algorithm that produces embeddings out of a knowledge graph. The knowledge graph has to be fed to the algorithm in a .csv format without index  and with specific headers i.e. 

- source: id of the source
- target: id of the target
- rel_type: type of the interaction

An example is available in data/kg_edgelist.csv. This knowledge graph is composed of 41k nodes of 4 types (functions, phenotype, drug and protein) and ~60 types of relationships.

KnoWalk need several dependencies, an environment named KnoWalk can be created by running

```
conda env create -f DLemb.yml
```
Then activate the environment with 


```
conda activate DLemb
```


The algorithm consists of a shallow neural network implemented in Keras, it is composed by an Embedding layer and a Normalized Dot layer. It works by randomly generating negative (wrong) triplets that are used to train the network: once the Dot product is computed the error is calculated trough RMSE and the weights of the embedding layer are optimized trouhg Adam optimization.

The customizable flags of DLemb can be listed by running: 

```
python3 DLemb.py -h
```
DLemb automatically runs on GPU is available. To run the tool the following command can be run.

```
python DLemb.py -i data/kg_edgelist.csv -o outputs/kg_embeddings.pickle
```







