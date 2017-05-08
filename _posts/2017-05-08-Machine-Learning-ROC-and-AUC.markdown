---
layout: post
title:  ROC and AUC 
date:   2017-05-08 15:03:00 +0800
categories: Machine_Learning
tag: ROC_and_AUC
---

* content
{:toc}


#How to judge a binary classifier's performance？ 
##Precision,Recall,F-score:
![fpr-and-tpr!]({{ '/styles/images/fpr-and-tpr.png' | prepend: site.baseurl }})
##ROC,AUC
###ROC(Receiver Operating Characteristic)
![fpr-and-tpr!]({{ '/styles/images/Roccurves.png' | prepend: site.baseurl }})
x-coordinate:EPR(false positive rate)
y-coordinate:TPR(true positive rate)
- Why use ROC?
  ROC curves have an attractive property: they are insensitive to changes in class distribution. If the proportion of positive to negative instances changes in a test set, the ROC curves will not change.
  ![fpr-and-tpr!]({{ '/styles/images/roc-and-precall.png' | prepend: site.baseurl }})
  ROC and precision-recall curves under class skew. 
  (a) ROC curves, 1:1; (b) precision-recall curves, 1:1; (c) ROC curves, 1:10 and (d) precision-recall curves, 1:10.
###AUC(Area Under Curve)
- Definition:The area under the ROC curve.
- Meaning:The AUC value is equivalent to the probability that a randomly chosen positive example is ranked higher than a randomly chosen negative example.
- Notice: Because random guessing produces the diagonal line between (0, 0) and (1, 1), which has an area of 0.5, no realistic classifier should have an AUC less than 0.5.