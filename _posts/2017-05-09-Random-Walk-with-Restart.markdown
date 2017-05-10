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