+++
# Date this page was created.
date = "2021-09-09"

# Project title.
title = "A Unified Speaker Adaptation Approach for ASR"

# Project summary to display on homepage.
summary = "A unified speaker adaptation approach consisting of feature adaptation and model adaptation for ASR."

# Optional image to display on homepage (relative to `static/img/` folder).
image_preview = ""

# Tags: can be used for filtering projects.
# Example: `tags = ["representation-learning"]`
tags = ["representation-learning"]

# Optional external URL for project (replaces project detail page).
external_link = ""
highlight = false
# Does the project detail page use math formatting?
math = false

# Optional featured image (relative to `static/img/` folder).
[header]
image = "asr.png"
caption = "Source: A Unified Speaker Adaptation Approach for ASR"

+++

[Follow the github repo](https://github.com/zyzpower/gradprune_speaker)

You will find the source code of the paper. 

This is the source code of our method proposed in paper "A Unified Speaker Adaptation Approach for ASR" accepted by EMNLP 2021.

We use the transformer model in Espnet toolkit as the model architecture, and the gradual pruning is achieved by editing code in espnet/espnet/asr/pytorch_backend/asr.py.


