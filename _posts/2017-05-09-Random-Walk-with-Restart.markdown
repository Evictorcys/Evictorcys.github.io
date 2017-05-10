---
layout: post
title:  Random Walk with Restart
date:   2017-05-09 21:48:00 +0800
categories: Rank
tag: Algorithm
---

* content
{:toc}


## Introduction

## Formula
随机游走是遍历图的一个随机过程，该过程收敛后会对应每个结点生成一个概率分布值，表示该结点被访问到的可能性。用T表示转移矩阵，T中的元素Tij表示从结点ei到结点ej的概率。Tij的计算公式如下：<br>
![Machine_learning_image1!]({{ '/styles/images/RWS_T.png' | prepend: site.baseurl }})
其中N(ei)表示与ei直接相连的结点集合，Wij表示结点ei和ej之间的权重（即这两个结点在知识库中的共现次数）。
用rt表示迭代t次时的概率分布，重启随机游走模型可用以下公式表示：<br>
![Machine_learning_image1!]({{ '/styles/images/RWS_R.png' | prepend: site.baseurl }})
其中s为初始向量，λ为重启概率。最终达到平稳分布如下所示：<br>
![Machine_learning_image1!]({{ '/styles/images/RWS_F.png' | prepend: site.baseurl }})


## Code
	import random
	import numpy as np
	def EntityRank(G, restart_rate, root, max_step):  
	'''
	Computer Walk
	'''
	    rank = dict()  
	    rank = {x:0 for x in G.keys()}  
	    rank[root] = 1  
	    #开始迭代  
	    for k in range(max_step):  
	        tmp = {x:0 for x in G.keys()}
	        total={x:0 for x in G.keys()}
	        #取节点i和它的出边尾节点集合ri  
	        for i, ri in G.items():
	            total[i]=sum(ri.values())
	            #取节点i的出边的权重和
	            for j, wij in ri.items():
	                #i是j的其中一条入边的首节点，因此需要遍历图找到j的入边的首节点，  
	                #这个遍历过程就是此处的2层for循环，一次遍历就是一次游走 
	                #if random.uniform(0,1)<=restart_rate:
	                tmp[root] = restart_rate
	                #else:       
	                tmp[j] += rank[i] * (wij/total[i])*(1-restart_rate)
	        rank = tmp  
	  
	        #输出每次迭代后各个节点的权重  
	        #print('iter: ' + str(k) + "\t"+str(rank)) 
	    return rank  

	def Cal_feature(G,restart_rate,root):
	'''
	Use formula
	'''
	    probability=np.zeros(shape=(len(G),len(G)))
	    total={x:0 for x in G.keys()}
	    Name=[x for x in G.keys()]
	    for i, ri in G.items():
	            total[i]=sum(ri.values())
	            #取节点i的出边的权重和
	            for j, wij in ri.items():
	                f=wij/total[i]
	                probability[Name.index(i)][Name.index(j)]=wij/total[i]
	    c=1-restart_rate
	    for m in range(len(G)):
	        probability[m][m]=1.0
	    new_probability=1-c*probability
	    print(new_probability)
	    S=[]
	    for x in G.keys():
	        if x == root:
	            S.append(1)
	        else:
	            S.append(0)
	    new_probability=np.linalg.inv(new_probability)
	    print(new_probability)
	    feature=restart_rate*np.dot(new_probability,S)
	    
	    return feature
	  
	if __name__ == '__main__' :  
	    G={"A":{"a1":1},
	       "B":{"b1":1,"b2":1},
	       "C":{"c1":1,"c2":1},
	       "a1":{"A":1,"d1":1},
	       "b1":{"B":1,"d2":1},
	       "b2":{"B":1},
	       "c1":{"C":1,"d1":1,"d2":1,"d3":1},
	       "c2":{"C":1,"d3":1},
	       "c3":{"C":1,"d3":1},
	       "d1":{"a1":1,"c1":1},
	       "d2":{"b1":1,"c1":1},
	       "d3":{"c1":1,"c2":1}}
	  
	    print(EntityRank(G, 0.5, 'A', 100))
	    print(Cal_feature(G,0.5,'A'))