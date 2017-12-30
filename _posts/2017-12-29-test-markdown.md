---
layout: post
title: cs231n 3 Loss function & Optimization
---

<script type="text/javascript"
   src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

## Loss function & Optimization
This leacture is mainly about different loss function and how ot optimize the loss function. Optimization: Make trade off between the fitness of trainning dataset and test dataset.

$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$
## Loss function: 
L = $$\frac{1}{N} \sum_{i}L_i(f(x_i,W), y_i)$$

### Multiclass SVM loss
SVM loss is called hinge loss too.

$$\sum_{j \neq y_j}max(0, s_i - s_{y_i} + 1)$$

{: .box-note}
**Note:** When W is samll, so all s is almost 0, the loss is the # of classes - 1 .

To optimize the loss function of SVM, we introduce a regularization loss, $$\lambda R(w)$$.
The loss function after regulatization is :
$$\sum_{j \neq y_j}max(0, s_i - s_{y_i} + 1) + \lambda R(W)$$

## Softmax classifier
Another optimization skill is softmax classifier. The fomula is as below.

$$L_i = -log(\frac{e^{s_{y_i}}}{\sum_{j}e^{s_j}})$$












