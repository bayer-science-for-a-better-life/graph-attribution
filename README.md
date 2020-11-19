Codebase for _Evaluating Attribution for Graph Neural Networks_.

![Schematic figure](media/TOC.png)

## Setup task, train GNN and evaluate attributions
If you want to get up and running attributions we recommend you run **notebooks/train_and_evaluate.ipynb** which sets up an attribution task, trains a GNN on a predictive task, and calculates attribution with several techniques and evaluates the attributions. At the end we can visually compare atrributions.

## Replicate results
If you want to replicate results from the [main publication][gnnatt] we recommend you run **notebooks/attribution_plot.ipynb**.

## What's implemented?

Attribution techniques:
* [Grad * Input][grad_times_input]
* [CAM (Class activation maps)][cam]
* [GradCAM (Gradient CAM)][gradcam]
* [SmoothGrad][smoothgrad]
* [Integrated Gradients][ig]
* [Attention weights][gat]

We test attribution on several GNN architectures by composing sequentially GNN blocks of different types:
* [GCN (Graph Convolution Network)][gcn], where we learn node embeddings.
* [GAT (Graph Attention Network)][gat], where message passing happens via an attention mechanism.
* [MPNN (Message Passing Network)][mpnn], where we learn node and edge embeddings.
* [GraphNets][graphnets], learning node, edge and global embeddings and conditioning each based on these learnt attributes.

## Test a new task or attribution method or model
To test out new ideas check out **graph_attribution/templates.py** which has all main abstract classes in the codebase. In particular **AttributionTask** is useful for tasks, **TransparentModel** for GNN models, **AttributionTechnique** for new attribution techniques.

# Code structure
The rest of the files are organized as:
* **data/** holds all datasets, one folder per task.
    * **data/dataset_bias** holds a folder for each spurious correlation task.
    * **data/results** holds CSV files with results from the [main publication][gnnatt].
    * **data/NOTICE** details properties of this data redistribution.
* **notebooks/** holds Jupyter notebooks.
* **graph_attribution/** holds the code for creating models, generating and evaluating attributions.

# Installing

The codebase is primarily a [Tensorflow 2.0](https://www.tensorflow.org/install) based framework that uses [Sonnet](https://github.com/deepmind/sonnet) and
[Graph Nets](https://github.com/deepmind/graph_nets) for building GNN models.

For generating new datasets we recommend using [Anaconda](https://www.anaconda.com/) for installing all dependencies. Requirements can be installed into a fresh conda environment:

```bash
$ conda env create -f environment.yml -n graph_attribution
```
Once installed you can run a notebook but running:
```bash
$ conda activate graph_attribution
$ jupyter notebook *.ipynb
```

# Giving Credit
If you use this code in your work, we ask that you cite our work. Here is an example
BibTex entry:

```
@article{NEURIPS2020_6054,
  title     = {Evaluating Attribution for Graph Neural Networks},
  author = {Benjamin Sanchez-Lengeling and Jennifer Wei and Brian Lee and Emily Reif and Wesley Qian and Yiliu Wang and Kevin James McCloskey and Lucy Colwell and Alexander B Wiltschko},
  booktitle = {Advances in Neural Information Processing Systems 33},
  year      = {2020},
  url       = {http://arxiv.org/abs/X},
}
```

# Related work
If you cite this work, you may also want to cite:

[McCloskey, K., Taly, A., Monti, F., Brenner, M. P. & Colwell, L. J. Using attribution to decode binding mechanism in neural network models for chemistry. Proc. Natl. Acad. Sci. U. S. A. 116, 11624–11629 (2019)][bias]
[Ying, Z., Bourgeois, D., You, J., Zitnik, M. & Leskovec, J. GNNExplainer: Generating Explanations for Graph Neural Networks. in Advances in Neural Information Processing Systems (eds. Wallach, H. et al.) vol. 32 9244–9255 (Curran Associates, Inc., 2019).][explainer]

[bias]: https://www.pnas.org/content/116/24/11624
[explainer]: https://arxiv.org/abs/1903.03894
[gnnatt]: https://arxiv.org/abs/X
[mpnn]: https://arxiv.org/abs/1704.01212
[gcn]: https://arxiv.org/abs/1509.09292
[graphnets]:arxiv.org/abs/1806.01261
[gat]: https://arxiv.org/abs/1710.10903
[grad_times_input]:https://arxiv.org/abs/1605.01713
[cam]: https://arxiv.org/abs/1512.04150
[gradcam]: https://arxiv.org/abs/1610.02391
[smoothgrad]: https://arxiv.org/abs/1706.03825
[ig]: https://arxiv.org/abs/1703.01365

This is not an official Google product.