+++
# Date this page was created.
date = "30/03/2022"

# Project title.
title = "Cross-model Back-translated Distillation for Unsupervised Machine Translation"

# Project summary to display on homepage.
summary = "A novel strategy to improve unsupervised MT by using back-translation with multiple models."

# Optional image to display on homepage (relative to `static/img/` folder).
image_preview = ""

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["machine-learning", "neural-machine-translation", "unsupervised"]

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

#### Accepted as conference paper at 38th International Conference on Machine Learning (ICML 2021).
#### Authors: Xuan-Phi Nguyen, Shafiq Joty, Thanh-Tung Nguyen, Wu Kui, Ai Ti Aw

[Github](https://nxphi47.github.io/publications/2021-multiagent-crosstranslated-unsupmt/)

Paper link: [https://arxiv.org/abs/1911.01986](https://arxiv.org/abs/1911.01986)

# Citation

Please cite as:

```bibtex
@incollection{nguyen2021cbd,
title = {Cross-model Back-translated Distillation for Unsupervised Machine Translation},
author = {Xuan-Phi Nguyen and Shafiq Joty and Thanh-Tung Nguyen and Wu Kui and Ai Ti Aw},
booktitle = {38th International Conference on Machine Learning},
year = {2021},
}
```

These guidelines demonstrate the steps to run CBD on the WMT En-De

### Finetuned model

Model | Train Dataset | Finetuned model
---|---|---
`WMT En-Fr` | [WMT English-French](not-ready) | model: [download](https://www.dropbox.com/s/qi02mbeh39cpow8/checkpoint1.infer.pth?dl=0) 
`WMT En-De` | [WMT English-German](not-ready) | model: [download](https://drive.google.com/file/d/1PEH6sW3Vp2RuwLLblJNxUm7L18zHgXhz/view?usp=sharing) 

#### 0. Installation

```bash
./install.sh
pip install fairseq==0.8.0 --progress-bar off
```

#### 1. Prepare data

Following instructions from [MASS-paper](https://github.com/microsoft/MASS) to create WMT En-De dataset.

#### 2. Prepare pretrained model

Download XLM finetuned model (theta_1): [here](https://drive.google.com/file/d/1EiJSwR49fD3N-iBpAsy0jv-18CdOd1sN/view?usp=sharing), save it to bash variable `export xlm_path=...`

Download MASS finetuned model (theta_2): [here](https://modelrelease.blob.core.windows.net/mass/mass_ft_ende_1024.pth), save it to `export mass_path=....`

Download XLM pretrained model (theta): [here](https://dl.fbaipublicfiles.com/XLM/mlm_ende_1024.pth), save it to `export pretrain_path...`


#### 3. Run CBD model
```bash

# you may change the inputs in the file according to your context
bash run_ende.sh

```

