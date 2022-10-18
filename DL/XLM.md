[TOC]


### 3.2 Masked Language Modeling

AKA cloze task

Randomly sample 15% of the BPE tokens, replace them by a [Mask] token 80% of the time, by a random token 10% of the time, and keep them unchanged 10% of the time.

Subsampling of frequent words:

- they usually provide less info than rare words
- their vector representation do not change significantly after training on several million examples

Method: each word is sampled by probability

$P(w_i) = \sqrt{\frac{t}{f(w_i)}}$

where $t$ is a chosen threshold, typically around $10^{−5}$. We chose this subsampling formula because it aggressively subsamples words whose frequency
is greater than $t$ while preserving the ranking of the frequencies.

