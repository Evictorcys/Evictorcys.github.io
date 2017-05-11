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
 - Hypothesis:![Machine_learning_image]({{'/styles/images/h_theta.png' | prepend: site.baseurl}})
 - ![Machine_learning_image]({{'/styles/images/theta_i.png' | prepend: site.baseurl}}):Parameters , but how to choose ![Machine_learning_image]({{'/styles/images/theta_i.png' | prepend: site.baseurl}})?
 - Minimize modeling error:
 - ![Machine_learning_image]({{'/styles/images/J_theta.png' | prepend: site.baseurl}})
# Gradient descent
 - ![Machine_learning_image]({{'/styles/images/theta_j.png' | prepend: site.baseurl}})
 - ![Machine_learning_image]({{'/styles/images/alpha.png' | prepend: site.baseurl}})= learning rate
 - Batch Gradient Descent:Each step of gradient descent uses all the training examples.
 - Stochastic gradient descent(SGD):Use one example in each iteration
 - Mini-batch Gradient descent:Use some examples in each iteration
![Machine_learning_image!]({{ '/styles/images/machine_learning2.png' | prepend: site.baseurl }})
 - Momentum:<br>
 Momentum is a method that helps accelerate SGD in the relevant direction and dampens oscillations. 
 - AdaGrad:<br>
 Adagrad is an algorithm for gradient-based optimization that does just this: It adapts the learning rate to the parameters, performing larger updates for infrequent and smaller updates for frequent parameters. For this reason, it is well-suited for dealing with sparse data. 
 - Adam:<br>
 Adaptive Moment Estimation (Adam) is another method that computes adaptive learning rates for each parameter. In addition to storing an exponentially decaying average of past squared gradients vt like Adadelta and RMSprop, Adam also keeps an exponentially decaying average of past gradients mt, similar to momentum.
![Machine_learning_image!]({{ '/styles/images/contours_evaluation_optimizers.gif' | prepend: site.baseurl }})![Machine_learning_image!]({{ '/styles/images/saddle_point_evaluation_optimizers.gif' | prepend: site.baseurl }})