# Differentiating Concepts and Instances for Knowledge Graph Embedding
Source code and datasets of EMNLP2018 paper: "Differentiating Concepts and Instances for Knowledge Graph Embedding".  https://arxiv.org/abs/1811.04588

## News
Thanks to [Shengding Hu](https://github.com/ShengdingHu) for providing the PyTorch version of the training code.

## Dataset
We provide YAGO39K and M-YAGO39K dataset we used in this work in data/YAGO39K directory. The meanings of these files are explained as follows:

data/YAGO39K/Train

* instance2id.txt, concept2id.txt, relation2id.txt: the id of every instance, concept and relation in this dataset.
* triple2id.txt: normal triples represented as ids with format [head_instance_id tail_instance_id relation_id].
* instanceOf2id.txt: instanceOf triples represented as ids with format [instance_id concept_id].
* subClassOf2id.txt: subClassOf triples represented as ids with format [sub_concept_id concept_id].

data/YAGO39K/Valid

* triple2id_positive.txt, instanceOf2id_positive.txt, subClassOf2id_positive.txt: positive triples from YAGO dataset. Their formats are the same as those in data/YAGO39K/Train.
* triple2id_negative.txt, instanceOf2id_negative.txt, subClassOf2id_negative.txt: negative triples generated by us, which will be used in Triple Classification experiments.

data/YAGO39K/Test

* the test dataset, which is similar to data/YAGO39K/Valid.

data/YAGO39K/M-Valid

* the valid dataset for M-YAGO39K. The formats of all files are the same as those in data/YAGO39K/Valid.

data/YAGO39K/M-Test

* the test dataset for M-YAGO39K. The formats of all files are the same as those in data/YAGO39K/Test.

## Codes
The source codes of our work are put in the folder src/.
## Compile

```shell
cd src
make
```

## Train


```shell
cd src
./transC
```

You can add the following optional parameters when running transC:

* -dim: the vector size.
* -margin: the margin for normal triples.
* -margin_ins: the margin for instanceOf triples.
* -margin_sub: the margin for subClassOf triples.
* -data: the dataset that you want to use. You can only choose YAGO39K in current vision. 
* -l1flag: it can be 1 or 0, 1 means using L1 loss and 0 means L2 loss.
* -bern: it can be 1 or 0, 1 means using "bern" strategy and 0 means using "unif" strategy.

The Vectors of entities, concepts and relations will be stored in the folder vector/ after training.

### Python Code
There is also python code for the training part, in py_version/
The python version can be run with

```
python -m py_version.transc
```

The outputs are stored in the same format and location with cpp version.

## Experiment

### Link Precidtion

For Link Prediction experiment, you need to

```shell
cd src
./test_link_prediction
```

You can add the following optional parameters when running test_link_prediction:

* -dim: the vector size.
* -data: the dataset that you want to use. You can only choose YAGO39K in current vision. 
* -threads: how many threads you want to use.

### Normal Triple Classification

For normal Triple Classification experiment, you need to

```shell
cd src
./test_classification_normal
```

You can add the following optional parameters when running test_triple_classification_normal:

- -dim: the vector size.
- -data: the dataset that you want to use. You can only choose YAGO39K in current vision. 

### InstanceOf and SubClassOf Triple Classification

For instanceOf and subClassOf Triple Classification experiments, you need to

```shell
cd src
./test_classification_isA
```

You can add the following optional parameters when running test_triple_classification_isA:

* -dim: the vector size.
* -data: the dataset that you want to use. You can only choose YAGO39K in current vision. 
* -mix: it can be 1 or 0, 1 means doing this experiment in M-YAGO39K and 0 means doing this experiment in YAGO39K.

## Cite
If you use the code, please cite this paper:

Xin Lv, Lei Hou, Juanzi Li, Zhiyuan Liu. Differentiating Concepts and Instances for Knowledge Graph Embedding. *The Conference on Empirical Methods in Natural Language Processing (EMNLP 2018)*L.
