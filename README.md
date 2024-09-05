# PDP-FADRL
Planning and optimizing O2O order delivery routes involves multiple depots, capacity constraints, time-window limitations, and pickup-delivery restrictions. The huge volume of transactions and computational demands further complicate the routing problem. We propose a novel feature fusion attention deep reinforcement learning model (FADRL) to overcome these constraints. Our innovative encoding and masking scheme efficiently handles multi-depot and multi-constraint scenarios. Furthermore, integrating self-attention with a Graph Neural Network (GNN) framework extends the existing research beyond unit square environments to real road networks.

# Dependencies
* Python>=3.8
* PyTorch>=1.7
* numpy
* tensorboard_logger
* tqdm

# Usage
## Reproducing Experimental Results
Due to GitHub's 25 MB file size limit, we have uploaded the entire package of source codes and datasets to OneDrive. This package includes all source codes, such as our proposed FADRL model and all baseline algorithms (DP, OR-Tools, LKH, Revised DRL-greedy, Revised DACT, FADRL_SUMO). Additionally, we have provided detailed documentation on the steps to obtain the experimental results for PDTSP, MDVRP, real road networks, and dynamic assignments.

[FADRL and All Baseline Modules](https://1drv.ms/f/c/d7c86f43ef725951/EhiamanLaxNHgIZ5iUH8V4oBqnmO1pYm365arq0gQC-AQQ?e=feouWH)

[Guide to Reproducing Experimental Results](https://1drv.ms/b/c/d7c86f43ef725951/ER-xhGUV-wNGn3nHnKdcE1ABB3eR1YSmxValDvL8TSCPQw?e=AWpRRm)
# Inference
<pre><code class="language-python">
--eval_only 
--load_path '{add pretrained model to load here}'
--T_max 3000 (The number of steps for inference)
--graph_size 20 (The number of visiting nodes)
--num_couriers 2 (The number of couriers)
--val_size 1000 
--val_batch_size 1000 
--val_dataset '{add dataset here}' 
--val_m 5 (The number of data augments for large scale problem)
</code></pre>


# Examples
## PDTSP-20
<pre><code class="language-python">
python run.py --eval_only --graph_size 20 --num_couriers 1 --T_max 1000 --val_m 1 --val_dataset "./datasets/pdp_20.pkl" --load_path "./pre-trained/pdtsp/20/epoch-156.pt
</code></pre>
## PDTSP-50
<pre><code class="language-python">
CUDA_VISIBLE_DEVICES=0,1 python run.py --eval_only --graph_size 50 --num_couriers 1 --T_max 1000 --val_m 1 --val_dataset "./datasets/pdp_50.pkl" --load_path "./pre-trained/pdtsp/50/epoch-196.pt
</code></pre>
## PDTSP-100
<pre><code class="language-python">
CUDA_VISIBLE_DEVICES=0,1,2 python run.py --eval_only --graph_size 100 --num_couriers 1 --T_max 1000 --val_m 2 --val_dataset "./datasets/pdp_100.pkl" --load_path "./pre-trained/pdtsp/100/epoch-195.pt" --val_size 1000 --val_batch_size 1000
</code></pre>
## VRP-20-2
<pre><code class="language-python">
python run.py --eval_only --graph_size 20 --num_couriers 2 --T_max 1000 --val_m 1  --load_path "pre-trained\vrp\vrp20.pt" --val_dataset  "./datasets/vrp_20.pkl" --val_size 1000 --val_batch_size 1000
</code></pre>
## VRP-50-5
<pre><code class="language-python">
CUDA_VISIBLE_DEVICES=0,1 python run.py --eval_only --graph_size 50 --num_couriers 5 --T_max 1000 --val_m 1  --load_path "pre-trained\vrp\vrp50.pt" --val_dataset  "./datasets/vrp_50.pkl" --val_size 1000 --val_batch_size 1000
</code></pre>
## VRP-100-10
<pre><code class="language-python">
CUDA_VISIBLE_DEVICES=0,1,2 python run.py --eval_only --graph_size 100 --num_couriers 10 --T_max 1000 --val_m 1  --load_path "pre-trained\vrp\vrp100.pt" --val_dataset  "./datasets/vrp_100.pkl" --val_size 1000 --val_batch_size 1000
</code></pre>
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

