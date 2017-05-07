---
layout: post
title:  Machine Learning Linear regression with one variable
date:   2017-05-07 15:05:00 +0800
categories: Machine_Learning
tag: Andrew_Ng
---

* content
{:toc}


# Model representation
## Notation:
 - m = Number of training examples
 - x's = "input" variable/features
 - y's = "output" variables/"target" variable
 - (x,y) = one training example
 - <img src="http://chart.googleapis.com/chart?cht=tx&chl= (x^i,y^i)" style="border:none;">= ith training example
 - h = hypothesis
![Machine_learning_image1!]({{ '/styles/images/machine_learning1.png' | prepend: site.baseurl }})
# Cost function
 - Hypothesis:<img src="http://chart.googleapis.com/chart?cht=tx&chl= h_\theta(x)=\theta_0\p\theta_1x" style="border:none;">
 - <img src="http://chart.googleapis.com/chart?cht=tx&chl= \theta_i" style="border:none;">:Parameters , but how to choose <img src="http://chart.googleapis.com/chart?cht=tx&chl= \theta_i" style="border:none;">?
 - - Minimize modeling error:
 - - - <img src="http://chart.googleapis.com/chart?cht=tx&chl= J(\theta_0,\theta_1)=\frac{1}{2m}\sum_{i=1}^{m}(h_\theta(x^{(i)}-y^{(i)}))^2" style="border:none;">
# Gradient descent
 - <img src="http://chart.googleapis.com/chart?cht=tx&chl= \theta_j:=\theta_j-\alpha\frac{\partial}{\partial\theta_j}J(\theta)" style="border:none;">
 - - <img src="http://chart.googleapis.com/chart?cht=tx&chl= \alpha" style="border:none;"> = learning rate
 - Batch Gradient Descent:
 - - Each step of gradient descent uses all the training examples.
