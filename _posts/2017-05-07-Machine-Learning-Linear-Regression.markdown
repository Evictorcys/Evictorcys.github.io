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
<img src="http://chart.googleapis.com/chart?cht=tx&chl= Hypothesis:h_\theta(x)=\theta_0 + \theta_1x" style="border:none;">
<img src="http://chart.googleapis.com/chart?cht=tx&chl= \theta_i" style="border:none;">:Parameters , but how to choose <img src="http://chart.googleapis.com/chart?cht=tx&chl= \theta_i" style="border:none;">?
 - Minimize modeling error:
# Gradient descent
