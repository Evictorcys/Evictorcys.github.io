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
 - ![Machine_learning_image]({{'/styles/images/x_i_y_i.png' | prepend: site.baseurl}})= ith training example
 - h = hypothesis
![Machine_learning_image1!]({{ '/styles/images/machine_learning1.png' | prepend: site.baseurl }})
# Cost function
 - Hypothesis:![Machine_learning_image]({{'/styles/images/h_x.png' | prepend: site.baseurl}})
 - ![Machine_learning_image]({{'/styles/images/theta_i.png' | prepend: site.baseurl}}):Parameters , but how to choose ![Machine_learning_image]({{'/styles/images/theta_i.png' | prepend: site.baseurl}})?
 - Minimize modeling error:
 - ![Machine_learning_image]({{'/styles/images/J_theta.png' | prepend: site.baseurl}})
# Gradient descent
 - ![Machine_learning_image]({{'/styles/images/theta_j.png' | prepend: site.baseurl}})
 - ![Machine_learning_image]({{'/styles/images/alpha.png' | prepend: site.baseurl}})= learning rate
 - Batch Gradient Descent:
 - Each step of gradient descent uses all the training examples.
![Machine_learning_image2!]({{ '/styles/images/machine_learning2.png' | prepend: site.baseurl }})
 - Stochastic gradient descent(SGD):
 - Momentum:
 - AdaGrad:
 - Adam: