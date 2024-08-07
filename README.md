# PDP-FADRL
We propose a novel deep reinforcement learning model (FADRL) incorporating feature fusion attention to overcome these constraints. Our innovative encoding and masking scheme efficiently handles multi-depot and multi-constraint scenarios. Furthermore, integrating self-attention with a Graph Neural Network (GNN) framework extends the existing research beyond unit square environments to real road networks.

# Dependencies
* Python>=3.8
* PyTorch>=1.7
* numpy
* tensorboard_logger
* tqdm

# Usage
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

