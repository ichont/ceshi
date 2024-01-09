# NeuralSZZ

## Project Description
This replication package contains the dataset and code for our paper `Neural SZZ Algorithm`.

we propose NEURALSZZ, a deep learning approach for detecting the root cause deletion lines in a bug-fixing commit and using them as input for the SZZ algorithm. NEURALSZZ first constructs
a heterogeneous graph attention network model that captures the semantic relationships between each deletion line and the other deletion and addition lines. To pinpoint the root cause of
a bug, NEURALSZZ uses a learning-to-rank technique to rank all deletion lines in the bug-fixing commit.

## Environments

1. OS: Ubuntu

   GPU: NVIDIA GTX 3090.

2. Language: Python (v3.7)

3. CUDA: 11.1

4. Torch: 1.11
   
5. other packages please refer to requirements.txt

## Directories

* ml_baseline: the machine learning baselines applied in our paper
* dl_baseline: the deep learning baseline applied in our paper
* key_degin: the ablation experiment
* pretrainedModel: our pre-trained model
* rawData: the original dataset, we download all original data from other papers here 
* processRawData: the code to process the raw data
* buildGraph: the code to build the heterogeneous graph
* trainData: the generated heterogeneous graph for each bug-fixing commit

## Files

* eval.py: some functions used to evaluate the effectiveness of our model
* genPyG.py: convert the graph in the trainData directory to PYG format
* genMiniGraphs.py: group all heterogeneous graphs in trainData into a single file for training
* genPairs.py: generate pairs for the ranknet model
* genBatch.py: combine multiple pairs into a batch
* model.py: the defined model
* train.py: train the model and get the result

## Train & Test
For running the cross fold validation and cross project prediction, run `train.py`.

For running the machine learning baselines, enter the ml_baseline directory and run `ml_baselines.py`.

For running the deep learning baselines, enter the dl_baseline directory and run `dl_baselines.py`.

For running the ablation study, enter the key_design directory and run `without_codebert.py` and `without_han.py`. 

## Data

### graph data

Each directory in trainData contains three files. The file `info.json` contains the repository's name, the bug-fixing commit and the bug-inducing commit. The file `graph1.json` contains the heterogeneous graph generated for the bug-fixing commit in json format. The file `graph2.json` contain our manual annotation result.

### final dataset

The files `dataset1.json`,`dataset2.json` and `dataset3.json` contain the filtered datasets for the DATASET1, DATASET2 and DATASET3 in our paper respectively.