# Adult-Confounded dataset
This repo contains data (and code for reproducing the data) for the
Adult-Confounded dataset, a variant of the [UCI-Adult dataset](https://archive.ics.uci.edu/ml/datasets/adult)
introduced in the paper [Environment Inference for Invariant Learning](https://arxiv.org/abs/2010.07249)

## Resampling the data
Open and run the notebook `generate_adult_confounded.ipynb`.

Running the notebook once samples a dataset with one correlation pattern.
In the paper we used train/test sets whose correlation patters differed.
Therefore to sample data from both distributions, look for a cell with the
following contents...
```python
"""Specify the subgroup here by selecting from catalog of functions above."""
CONFOUND_FN = corr_sg02_anti_sg13 # uncomment this to generate dist'n used for training
# CONFOUND_FN = corr_sg13_anti_sg02 # uncomment this to generate dist'n used for testing
```
...and run the notebook twice, one time for each confounding function.

## Using the data
In our experiments we trained using the file
`./data/adult_conf/corr_sg02_anti_sg13/train.csv`
and tested using the file
`./data/adult_conf/corr_sg13_anti_sg02/test.csv`

This correponds to a dramatic subgroup-label correlation at train time that is reversed at test time.

## Citing the dataset
If your research makes use of this dataset, please consider providing the following citation:
```BibTeX
@inproceedings{creager21environment,
  title={Environment Inference for Invariant Learning},
  author={Creager, Elliot and Jacobsen, J{\"o}rn-Henrik and Zemel, Richard},
  booktitle={International Conference on Machine Learning},
  year={2021},
}
```
