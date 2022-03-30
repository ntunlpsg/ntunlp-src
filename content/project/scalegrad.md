+++
# Date this page was created.
date = "2022-03-30"

# Project title.
title = "Straight to the Gradient: Learning to Use Novel Tokens for Neural Text Generation"

# Project summary to display on homepage.
summary = "A novel training objective for text generation"

# Optional image to display on homepage (relative to `static/img/` folder).
image_preview = ""

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["text-generation"]

# Optional external URL for project (replaces project detail page).
external_link = ""

# Does the project detail page use math formatting?
math = false
highlight = false
# put a link to your preferred image that will be the banner of the page.
[header]
image = ""
caption = ""

+++

[github](https://github.com/shawnlimn/ScaleGrad)

Source code for [Straight to the Gradient: Learning to Use Novel Tokens for Neural Text Generation](http://proceedings.mlr.press/v139/lin21b/lin21b.pdf)

- Xiang Lin, Simeng Han and Shafiq Joty 

Accepted at 38th International Conference on Machine Learning (**ICML'21**).

The repo is adapted from [Neural Unlikelihood Training](https://github.com/facebookresearch/unlikelihood_training/). You could either follow the original repo or the instruction below to finish installing the dependencies. 



## Setup

### Dependencies

The implementation is a custom [fairseq](https://github.com/pytorch/fairseq) module. Download and install fairseq:

```bash
git clone https://github.com/pytorch/fairseq.git
cd fairseq
pip install --editable .
```

Install other dependencies:

```bash
pip install nltk
pip install pytorch-transformers  
```

### 'Installing' the a customised module for ScaeGrad

Copy the `custom` directory in this repo into the `fairseq` repo that you downloaded above:

```bash
export FAIRSEQ_DIR=/path/to/fairseq
export SCALEGRAD_DIR=/path/to/ScaleGrad

cp -r $SCALEGRAD_DIR/custom $FAIRSEQ_DIR/fairseq
```



## Finetuning GPT-2 for Language Modeling and Auto Completion

We assume that you are in the `fairseq` base directory.

### Dataset

Download and unpack the BPE-tokenized WikiText:

```bash
wget https://dl.fbaipublicfiles.com/unlikelihood/wikitext-103-bpe_v0.tar.gz
tar -xzvf wikitext-103-bpe_v0.tar.gz
mv wikitext-103-bpe_v0 data-bin/
```

### Finetuning with ScaleGrad/MLE:

`gamma` is the only hyper-parameter needed to be pre-determined. `gamma=1` is equivalent to performing MLE finetuning. In our paper, we experimented with three different choices from \{0.2,0.5,0.8\}.

```bash
python fairseq/custom/gpt2/run_gpt2.py  \
--data-base ./data-bin/wikitext-103-bpe_v0    \
--output-dir ./checkpoint/gpt-2   \
--eval-split valid    \
--train-n-steps 35000   \
--validate-every 1000    \
--mode train \
--train-batch-size 300    \
--gamma 0.2 \
--learning-rate 2e-5 \
--seed 60 
```

### Evaluation

```
python fairseq/custom/gpt2/run_gpt2.py  \
    --data-base ./data-bin/wikitext-103-bpe_v0 \
    --output-dir ./checkpoint/gpt2/sg_output \
    --eval-split test \
    --model-load-dir ./checkpoint/gpt2/sg/best \
    --mode eval-both
```

We used a single GTX 2080Ti gpu.


## Citation

Please cite our work if you found the resources in this repository useful:

```
@InProceedings{lin-2021-straight,
  title = 	 {Straight to the Gradient: Learning to Use Novel Tokens for Neural Text Generation},
  author =       {Lin, Xiang and Han, Simeng and Joty, Shafiq},
  booktitle = 	 {Proceedings of the 38th International Conference on Machine Learning},
  pages = 	 {6642--6653},
  year = 	 {2021},
  editor = 	 {Meila, Marina and Zhang, Tong},
  volume = 	 {139},
  series = 	 {Proceedings of Machine Learning Research},
  month = 	 {18--24 Jul},
  publisher =    {PMLR},
  pdf = 	 {http://proceedings.mlr.press/v139/lin21b/lin21b.pdf},
  url = 	 {http://proceedings.mlr.press/v139/lin21b.html},
  abstract = 	 {}
}


```

## 


