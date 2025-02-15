# Predicting Organic Reaction Outcomes with Weisfeiler-Lehman Network

This repository contains the data and codes of the paper:

*Predicting Organic Reaction Outcomes with Weisfeiler-Lehman Network (NIPS 2017)* [PDF](https://arxiv.org/abs/1709.04555)

## Updated Version
We have updated our reaction predictor model and improved the results (shown in the table 1). The new github repo link is here: https://github.com/connorcoley/rexgen_direct. We suggest you to use the updated repo because it is written in  tensorflow version 1.3.0 (rather than 0.12.0). 

<img src="https://github.com/wengong-jin/nips17-rexgen/blob/master/result.png" width="800">

## Data
* USPTO-15K/data.zip contains the train/dev/test split of USPTO-15K dataset used in our paper, borrowed from [Coley et al.](http://pubs.acs.org/doi/abs/10.1021/acscentsci.7b00064) Each line in the file has two fields, separated by space:
  * Reaction smiles (products are not atom mapped)
  * Four types of reaction edits: 
    1. Atoms lost Hydrogens
    2. Atoms obtained Hydrogens
    3. Deleted bonds
    4. Added bonds
    
    The first two subfields contains a list of atom. The last two subfields includes a list of triples in the form of (atom1-atom2-bondtype). All atoms are indicated by their atom map numbers given in the reaction smiles. See the following table for all possible bond types:
    
  | Bond Type | Bond Name    |
  | ------    |:------------:|
  | 1.0       | Single bond  |
  | 2.0       | Double bond  |
  | 3.0       | Triple bond  |
  | 1.5       | Aromatic bond|

* USPTO/data.zip includes the train/dev/test split of USPTO dataset used in our paper. It has in total 480K fully atom mapped reactions. Each line in the file has two fields, separated by space:
  * Reaction smiles (both reactants and products are atom mapped)
  * Reaction center. That is, atom pairs whose bonds in between changed in the reaction. Atoms are represented by their atom map number given in the reaction smiles.

* human/ directory contains the 80 reactions used in our human study.
  
## Codes
Training and testing codes are in respective repositories:
* core-wln-global/ includes codes for reaction core identification (referred as global model in the paper).
* rank-wln/ includes codes for WLN + sum-pooling in the paper for candidate ranking
* rank-diff-wln/ includes codes for WL Difference Network (WLDN) for candidate ranking

Sample usage are provided in USPTO/README.md, which also applies to USPTO-15K. We used tensorflow-0.12.1 for development:

https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-0.12.1-cp27-none-linux_x86_64.whl

## Contributors
Wengong Jin (wengong@csail.mit.edu)

Connor W. Coley (ccoley@mit.edu)
