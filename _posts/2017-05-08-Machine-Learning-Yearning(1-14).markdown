---
layout: post
title:  Machine Learning Yearning(1-14)  
date:   2017-05-08 15:03:00 +0800
categories: Machine_Learning
tag: Andrew Ng
---

* content
{:toc}


#### Why dev and test sets should come from the same distribution?
- Beacause once you define the dev and test sets, your team will be focused on improving dev set performance.Thus, the dev set should reflect the task you want most to improve on.
- Suppose your team develops a system that works well on the dev set but not the test set. If your dev and test sets had come from the same distribution, then you would have a very clear diagnosis of what went wrong: You have overfit the dev set. The obvious cure is to get more dev set data. But if the dev and test sets come from different distributions, then your options are less clear. Several things could have gone wrong:
	1. You had overfit to the dev set.
	2. The test set is harder than the dev set. So your algorithm might be doing as well as could be expected, and there’s no further significant improvement is possible.
	3. The test set is not necessarily harder, but just different, from the dev set. So what works well on the dev set just does not work well on the test set. In this case, a lot of your work to improve dev set performance might be wasted effort.

#### How large do the dev/test sets need to be?
- The dev set should be large enough to detect differences between algorithms that you are trying out. For example, if classifier A has an accuracy of 90.0% and classifier B has an accuracy of 90.1%, then a dev set of 100 examples would not be able to detect this 0.1% difference. Compared to other machine learning problems I’ve seen, a 100 example dev set is small. Dev sets with sizes from 1,000 to 10,000 examples are common. With 10,000 examples, you will have a good chance of detecting an improvement of 0.01%.
- The test set should be large enough to give high confidence in the overall performance of your system. One popular heuristic had been to use 30% of your data for your test set. This works well when you have a modest number of examples—say 100 to 10,000 examples. But in the era of big data where we now have machine learning problems with sometimes more than a billion examples, the fraction of data allocated to dev/test sets has been shrinking, even as the absolute number of examples in the dev/test sets has been growing. There is no need to have excessively large dev/test beyond what is needed to evaluate the performance of your algorithms.

#### Error analysis
- The process of looking at misclassified examples.