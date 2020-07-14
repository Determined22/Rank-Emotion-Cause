# Rank-Emotion-Cause

This repo contains the code of the following paper:

**Effective Inter-Clause Modeling for End-to-End Emotion-Cause Pair Extraction**. In *Proc. of ACL 2020: The 58th Annual Meeting of the Association for Computational Linguistics*, pages 3171--3181. [[link](https://www.aclweb.org/anthology/2020.acl-main.289/)] 

<br>

## Results

Experimental results with two different data splits: 

- The first split is 10-fold cross-validation (located in `data/split10/`), following [NUSTM/ECPE](https://github.com/NUSTM/ECPE). 
- The second split is based on randomly sampling train/validation/test sets with 8:1:1 proportion 20 times (located in `data/split20/`), following [HLT-HITSZ/TransECPE](https://github.com/HLT-HITSZ/TransECPE). 

|      Split       |    Emotion-Cause Pair Extraction     |  Emotion Clause Extraction   |   Cause Clause Extraction    |
| :--------------: | :----------------------------------: | :--------------------------: | :--------------------------: |
|    10-fold cv    |   **F=0.7360**, P=0.7119, R=0.7630   | F=0.9057, P=0.9123, R=0.8999 | F=0.7615, P=0.7461, R=0.7788 |
| 8:1:1 (20 times) | **F=0.6915**, P=0.6575, R=0.7305 | F=0.8942, P=0.8936, R=0.8948 | F=0.7191, P=0.6940, R=0.7471 |
|                  |                                      |                              |                              |

<br>

## Requirements

- Python 3
- PyTorch 1.2.0
- [Transformers from Hugging Face](https://github.com/huggingface/transformers)

With Anaconda, we can create the environment with the provided `environment.yml`:

```bash
conda env create --file environment.yml 
conda activate EmoCau
```

The code has been tested on Ubuntu 16.04 using a single GPU. For multi-GPU training, a little extra work may be needed, and please refer to these examples: [Hugging Face](https://github.com/huggingface/transformers/blob/master/src/transformers/trainer.py) and [CLUEbenchmark](https://github.com/CLUEbenchmark/CLUE/tree/master/baselines/models_pytorch). 

<br>

## Quick Start

1. Clone or download this repo.

2. Download the pertrained ["BERT-Base, Chinese"](https://github.com/google-research/bert) model from [this link](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-chinese.tar.gz). And then put the model file `pytorch_model.bin` to the folder `src/bert-base-chinese`.  

3. Run our model *RankCP*:

```bash
python src/main.py
```

