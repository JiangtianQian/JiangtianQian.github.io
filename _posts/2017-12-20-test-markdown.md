---
layout: post
title: cs231n 3 Loss function & Optimization
---

This leacture is mainly about different loss function and how ot optimize the loss function. Optimization: Make trade off between the fitness of trainning dataset and test dataset.

### Multiclass SVM loss

~~~
L(i) = sum(max(0, s(j) - s(yi) + 1))
~~~

{: .box-note}
**Note:** When W is samll, so all s is almost 0, the loss is the # of classes - 1.

## Softmax classifier
~~~
L(i) = -log(...)
~~~









