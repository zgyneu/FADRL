# PDP-FADRL
We propose a novel deep reinforcement learning model (FADRL) incorporating feature fusion attention to overcome these constraints. Our innovative encoding and masking scheme efficiently handles multi-depot and multi-constraint scenarios. Furthermore, integrating self-attention with a Graph Neural Network (GNN) framework extends the existing research beyond unit square environments to real road networks.

# Dependencies
* Python>=3.8
* PyTorch>=1.7
* numpy
* tensorboard_logger
* tqdm

# Usage
## Reproducing Experimental Results
Due to GitHub's 25 MB file size limit, we have uploaded the entire package of source codes and datasets to OneDrive. This package includes all source codes, such as our proposed FADRL model and all baseline algorithms (DP, OR-Tools, LKH, Revised DRL-greedy, Revised DACT). Additionally, we have provided detailed documentation on the steps to obtain the experimental results for PDTSP, MDVRP, real road networks, and dynamic assignments.

[OneDrive Link Here]([(https://1drv.ms/f/c/d7c86f43ef725951/EhiamanLaxNHgIZ5iUH8V4oBqnmO1pYm365arq0gQC-AQQ?e=feouWH)])

## Generating data
Training data is generated randomly when training and testing the model. 

## Training
### PDTSP examples

Modify the options.py using the following values.
20 nodes:
 --problem pdtsp --graph_size 20 --warm_up 2 --max_grad_norm 0.05 --val_m 1 

50 nodes:
 --problem pdtsp --graph_size 50 --warm_up 1.5 --max_grad_norm 0.15 --val_m 1 

100 nodes:
 --problem pdtsp --graph_size 100 --warm_up 1 --max_grad_norm 0.2 --val_m 1 

### VRP examples
Modify the options.py using the following values.
20 nodes:
 --problem vrp --graph_size 20 --num_couriers 2 --warm_up 2 --max_grad_norm 0.05 --val_m 1 

50 nodes:
 --problem vrp --graph_size 50 --num_couriers 5 --warm_up 1.5 --max_grad_norm 0.15 --val_m 1 

100 nodes:
 --problem vrp --graph_size 100 --num_couriers 10 --warm_up 1 --max_grad_norm 0.2 --val_m 1 

