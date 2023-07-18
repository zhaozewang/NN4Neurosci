# Neural Networks for Neuroscience
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PyPI version](https://badge.fury.io/py/nn4n.svg)](https://badge.fury.io/py/nn4n)
<br>
Some of the most commonly used the NN architectures in neuroscience research are included in this project to ease the implementation process.

## Table of contents
- [Install](#install)
    - [Install From GitHub](#install-from-github)
- [Model](#model)
    - [CTRNN (Continuous-Time RNN)](#CTRNN)
- [Structure](#structure)
    - [Mult-Area RNN w/o EI Constraints](#singlemulti-area-rnn-wo-ei-constraints)


## Install
### Install from GitHub
```
git clone https://github.com/zhaozewang/NN4Neurosci.git
```
#### Install using command line
```
cd NN4Neurosci/
python setup.py install
```
#### Install using pip
```
cd NN4Neurosci/
pip install .
```


## Model
### CTRNN
The implementation of standard continuour-time RNN (CTRNN). This implementation also supports adding Excitator-Inhibitory contraints proposed in [Training Excitatory-Inhibitory Recurrent Neural Networks for Cognitive Tasks: A Simple and Flexible Framework](https://doi.org/10.1371/journal.pcbi.1004792) by Song et al. 2016.

- [Documentation](./docs/CTRNN.md)
- [Examples](./examples/CTRNN.ipynb)

## Structure
The detailed structure (e.g. whether its modular or hierarchical etc.) of any standard 3-layer RNN (as shown below) can be specified using masks in our `model` module implementation. Easy implementations of a few RNN structures is included in the `structure` module.

<p align="center"><img src="./img/RNN_structure.png" width="400"></p>

### Single/Multi-Area RNN w/o EI Constraints
The HiddenLayer of a RNN is often defined using a connectivity matrix, depicting a somewhat 'random' connectivity between neurons. The connectivity matrix is often designed to imitate the connectivity of a certain brain area or a few brain areas. When modeling a single brain area, the connectivity matrix is often a square matrix. When modeling multiple brain areas, the connectivity matrix is often a block matrix, where each block represents the connectivity of a single brain area.<br>
The implementation of both Single-Area RNN and Multi-Area RNN can be easily achieved using the [MultiArea](./nn4n/structure/multi_area.py) class. An Multi-Area RNN that supports E/I constraints is also included in [MultiAreaEI](./nn4n/structure/multi_area_ei.py) class.

- [Documentation](./docs/structure.md)
- [Examples](./examples/MultiArea.ipynb)


## Criterion
### RNNLoss
The loss function is modularized. Each criterion is designed in the format of $\lambda_L L(\cdot)$. By default, all $\lambda_{*}$ are set to 0 and won't be added to loss (nor the auto-grad tree). By changing the corresponding $\lambda_{*}$ to non-zero positive values, the corresponding loss function will be added to the total loss. The total loss is the sum of all loss functions with non-zero $\lambda_{*}$.
- [Documentation](./docs/criterion.md)

## Others
For similar projects: 
- [nn-brain](https://github.com/gyyang/nn-brain)

## Acknowledgements
Immense thanks to Christopher J. Cueva for his mentorship in developing this project. This project can't be done without his invaluable help.