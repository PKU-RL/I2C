# I2C

Written by Ziluo Ding and Zongqing Lu

**Peking University**.

### Table of Contents
1. [Introduction](#introduction)
2. [Dependencies](#dependencies)
3. [Applications](#applications)
4. [Issues](#issues)
5. [Citation](#citation)

### Introduction

DGN is graph convolutional reinforcement learning, where the multi-agent environment is modeled as a graph, each agent is a node, and the encoding of local observation of agent is the feature of node. We apply convolution to the graph of agents. By employing multi-head attention as the convolution kernel, graph convolution is able to extract the relation representation between nodes and convolve the features from neighboring nodes just like a neuron in a convolutional neural network (CNN). Latent features extracted from gradually increased receptive fields are exploited to learn cooperative policies. Moreover, the relation representation is temporally regularized to help the agent develop consistent cooperative policy.

<img src="arch.png" alt="DGN" width="500">

The codes are the implementations of DGN in the three scenarios, i.e., Jungle, Battle and Routing, presented in the paper
[Graph Convolution Reinforcement Learning](https://arxiv.org/abs/1810.09202)

In DGN, all agents share weights for the modules. The main reason is that agents use relation kernels to extract their relations based the encodings of their observations. If the encoders are different (agents encodes the observation in different ways), the relation kernels can hardly learn to extract their relations since the graph of agents is highly dynamic. 

Another very important benefit comes from parameter-sharing among agents is **DGN can naturally avoid non-stationarity.** From the optimization point of view, DGN optimizes a set of parameters for N objectives, one objective for each agent. As illustrated in the figure above, DGN as a whole can be seen as taking all the observations as input and outputting actions for all the agents, and thus DGN implicitly avoids the non-stationarity. 


### Dependencies

Install dependencies using pip.

```shell
python -m pip install -r requirements.txt
```


### Applications

DGN is simple and efficient. It empirically outperforms many state-of-art algorithms. DGN is applicable to many real applications. DGN has been applied to:
* **Traffic signal control** by researchers from Penn State ([CoLight: Learning Network-level Cooperation for Traffic Signal Control](https://arxiv.org/abs/1905.05717)). 

We expect DGN will be widely applied to many more applications. 


### Citation

If you are using the codes, please cite our paper.

[Ziluo Ding, Tiejun Huang, and Zongqing Lu. *Learning Individually Inferred Communication for Multi-Agent Cooperation*. NeurIPS'20.](https://arxiv.org/abs/2006.06455)

	@inproceedings{ding2020learning,
        	title={Learning Individually Inferred Communication for Multi-Agent Cooperation},
        	author={Ding, Ziluo and Huang, Tiejun and Lu, Zongqing},
        	booktitle={NeurIPS},
        	year={2020}
	}
