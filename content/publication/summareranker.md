+++
abstract = "Sequence-to-sequence neural networks have recently achieved great success in abstractive summarization, especially through fine-tuning large pre-trained language models on the downstream dataset. These models are typically decoded with beam search to generate a unique summary. However, the search space is very large, and with the exposure bias, such decoding is not optimal. In this paper, we show that it is possible to directly train a second-stage model performing re-ranking on a set of summary candidates. Our mixture-of-experts SummaReranker learns to select a better candidate and consistently improves the performance of the base model. With a base PEGASUS, we push ROUGE scores by 5.44% on CNN-DailyMail (47.16 ROUGE-1), 1.31% on XSum (48.12 ROUGE-1) and 9.34% on Reddit TIFU (29.83 ROUGE-1), reaching a newstate-of-the-art." 
authors = ["Mathieu Ravaut", "Shafiq Joty", "Nancy F. Chen"]
date = "2022-03-30"
image = ""
image_preview = ""
math = false
publication_types = ["1"]
selected = true
publication = "60th Annual Meeting of the Association for Computational Linguistics (ACL 2022)"
title = "SummaReranker: A Multi-Task Mixture-of-Experts Re-ranking Framework for Abstractive Summarization"
url_code = "https://github.com/ntunlp/SummaReranker"
url_dataset = ""
url_pdf = "https://arxiv.org/pdf/2203.06569.pdf"
url_project = ""
url_slides = ""
url_video = ""
+++ 