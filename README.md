[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Build Status](https://github.com/PaccMann/paccmann_predictor/actions/workflows/build.yml/badge.svg)](https://github.com/PaccMann/paccmann_predictor/actions/workflows/build.yml)

# paccmann_predictor

Drug interaction prediction with PaccMann.

`paccmann_predictor` is a package for drug interaction prediction, with examples of 
anticancer drug sensitivity prediction and drug target affinity prediction. Please see our papers:

- [_Toward explainable anticancer compound sensitivity prediction via multimodal attention-based convolutional encoders_](https://doi.org/10.1021/acs.molpharmaceut.9b00520) (*Molecular Pharmaceutics*, 2019). This is the original paper on IC50 prediction using drug properties and tissue-specific cell line information (gene expression profiles). While the original code was written in `tensorflow` and is available [here](https://github.com/drugilsberg/paccmann), this is the `pytorch` implementation of the best PaccMann architecture (multiscale convolutional encoder).

- [Data-driven molecular design for discovery and synthesis of novel ligands: a case study on SARS-CoV-2](https://iopscience.iop.org/article/10.1088/2632-2153/abe808) (_Machine Learning: Science and Technology_, 2021). In there, we propose a slightly modified version to predict drug-target binding affinities based on protein sequences and SMILES


*NOTE*: PaccMann acronyms "Prediction of AntiCancer Compound sensitivity with Multi-modal Attention-based Neural Networks".

**PaccMann for affinity prediction:**
![Graphical abstract](https://github.com/PaccMann/paccmann_predictor/blob/master/assets/paccmann.png "Graphical abstract")


## Requirements

- `conda>=3.7`

## Installation

The library itself has few dependencies (see [setup.py](setup.py)) with loose requirements. 
To run the example training script we provide environment files under `examples/IC50/`.

Create a conda environment:

```sh
conda env create -f examples/IC50/conda.yml
```

Activate the environment:

```sh
conda activate paccmann_predictor
```

Install in editable mode for development:

```sh
pip install -e .
```

## Example usage

In the `examples` directory is a training script [train_paccmann.py](./examples/IC50/train_paccmann.py) that makes use
of `paccmann_predictor`.

```console
(paccmann_predictor) $ python examples/IC50/train_paccmann.py -h
usage: train_paccmann.py [-h]
                         train_sensitivity_filepath test_sensitivity_filepath
                         gep_filepath smi_filepath gene_filepath
                         smiles_language_filepath model_path params_filepath
                         training_name

positional arguments:
  train_sensitivity_filepath
                        Path to the drug sensitivity (IC50) data.
  test_sensitivity_filepath
                        Path to the drug sensitivity (IC50) data.
  gep_filepath          Path to the gene expression profile data.
  smi_filepath          Path to the SMILES data.
  gene_filepath         Path to a pickle object containing list of genes.
  smiles_language_filepath
                        Path to a pickle object a SMILES language object.
  model_path            Directory where the model will be stored.
  params_filepath       Path to the parameter file.
  training_name         Name for the training.

optional arguments:
  -h, --help            show this help message and exit
```

`params_filepath` could point to [examples/IC50/example_params.json](examples/IC50/example_params.json), examples for other files can be downloaded from [here](https://ibm.box.com/v/paccmann-pytoda-data).

## References

If you use `paccmann_predictor` in your projects, please cite the following:

```bib
@article{manica2019paccmann,
  title={Toward explainable anticancer compound sensitivity prediction via multimodal attention-based convolutional encoders},
  author={Manica, Matteo and Oskooei, Ali and Born, Jannis and Subramanian, Vigneshwari and S{\'a}ez-Rodr{\'\i}guez, Julio and Mart{\'\i}nez, Mar{\'\i}a Rodr{\'\i}guez},
  journal={Molecular pharmaceutics},
  volume={16},
  number={12},
  pages={4797--4806},
  year={2019},
  publisher={ACS Publications},
  doi = {10.1021/acs.molpharmaceut.9b00520},
  note = {PMID: 31618586}
}

@article{born2021datadriven,
  author = {Born, Jannis and Manica, Matteo and Cadow, Joris and Markert, Greta and Mill, Nil Adell and Filipavicius, Modestas and Janakarajan, Nikita and Cardinale, Antonio and Laino, Teodoro and {Rodr{\'{i}}guez Mart{\'{i}}nez}, Mar{\'{i}}a},
  doi = {10.1088/2632-2153/abe808},
  issn = {2632-2153},
  journal = {Machine Learning: Science and Technology},
  number = {2},
  pages = {025024},
  title = {{Data-driven molecular design for discovery and synthesis of novel ligands: a case study on SARS-CoV-2}},
  url = {https://iopscience.iop.org/article/10.1088/2632-2153/abe808},
  volume = {2},
  year = {2021}
}
```
