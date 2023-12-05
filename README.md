# AiZynthFinder

[![License](https://img.shields.io/github/license/MolecularAI/aizynthfinder)](https://github.com/MolecularAI/aizynthfinder/blob/master/LICENSE)
[![Tests](https://github.com/MolecularAI/aizynthfinder/workflows/tests/badge.svg)](https://github.com/MolecularAI/aizynthfinder/actions?workflow=tests)
[![codecov](https://codecov.io/gh/MolecularAI/aizynthfinder/branch/master/graph/badge.svg)](https://codecov.io/gh/MolecularAI/aizynthfinder)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/python/black) 
[![version](https://img.shields.io/github/v/release/MolecularAI/aizynthfinder)](https://github.com/MolecularAI/aizynthfinder/releases)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MolecularAI/aizynthfinder/blob/master/contrib/notebook.ipynb)

AiZynthFinder is a tool for retrosynthetic planning. The default algorithm is based on a Monte Carlo tree search that recursively breaks down a molecule to purchasable precursors. The tree search is guided by a policy that suggests possible precursors by utilizing a neural network trained on a library of known reaction templates. This setup is completely customizable as the tool
supports multiple search algorithms and expansion policies.

An introduction video can be found here: [https://youtu.be/r9Dsxm-mcgA](https://youtu.be/r9Dsxm-mcgA)

## Prerequisites

Before you begin, ensure you have met the following requirements:

* Linux, Windows or macOS platforms are supported - as long as the dependencies are supported on these platforms.

* You have installed [anaconda](https://www.anaconda.com/) or [miniconda](https://docs.conda.io/en/latest/miniconda.html) with python 3.9 - 3.11

The tool has been developed on a Linux platform, but the software has been tested on Windows 10 and macOS Catalina.

## Installation

First clone the repository using Git.

Then execute the following commands in the root of the repository 

    conda env create -f env-dev.yml
    conda activate aizynth-dev
    poetry install --all-extras
    
the `aizynthfinder` package is now installed in editable mode.


## Usage

The tool will install the `aizynthcli` and `aizynthapp` tools
as interfaces to the algorithm:

    aizynthcli --config config_local.yml --smiles smiles.txt
    aizynthapp --config config_local.yml


Consult the documentation [here](https://molecularai.github.io/aizynthfinder/) for more information.

To use the tool you need

    1. A stock file
    2. A trained expansion policy network
    3. A trained filter policy network (optional)
    
Such files can be downloaded from [figshare](https://figshare.com/articles/AiZynthFinder_a_fast_robust_and_flexible_open-source_software_for_retrosynthetic_planning/12334577) and [here](https://figshare.com/articles/dataset/A_quick_policy_to_filter_reactions_based_on_feasibility_in_AI-guided_retrosynthetic_planning/13280507) or they can be downloaded automatically using

```
download_public_data my_folder
```

where ``my_folder`` is the folder that you want download to.
This will create a ``config.yml`` file that you can use with either ``aizynthcli`` or ``aizynthapp``.

## Development

### Testing

Tests uses the ``pytest`` package, and is installed by `poetry`

Run the tests using:

    pytest -v

The full command run on the CI server is available through an `invoke` command

    invoke full-tests
    
 ### Documentation generation

The documentation is generated by Sphinx from hand-written tutorials and docstrings

The HTML documentation can be generated by

    invoke build-docs

## Contributing

We welcome contributions, in the form of issues or pull requests.

If you have a question or want to report a bug, please submit an issue.


To contribute with code to the project, follow these steps:

1. Fork this repository.
2. Create a branch: `git checkout -b <branch_name>`.
3. Make your changes and commit them: `git commit -m '<commit_message>'`
4. Push to the remote branch: `git push`
5. Create the pull request.

Please use ``black`` package for formatting, and follow ``pep8`` style guide.


## Contributors

* [@SGenheden](https://www.github.com/SGenheden)
* [@lakshidaa](https://github.com/Lakshidaa)
* Helen Lai
* [@EBjerrum](https://www.github.com/EBjerrum)
* [@A-Thakkar](https://www.github.com/A-Thakkar)
* [@benteb](https://www.github.com/benteb)

The contributors have limited time for support questions, but please do not hesitate to submit an issue (see above).

## License

The software is licensed under the MIT license (see LICENSE file), and is free and provided as-is.

## References

1. Thakkar A, Kogej T, Reymond J-L, et al (2019) Datasets and their influence on the development of computer assisted synthesis planning tools in the pharmaceutical domain. Chem Sci. https://doi.org/10.1039/C9SC04944D
2. Genheden S, Thakkar A, Chadimova V, et al (2020) AiZynthFinder: a fast, robust and flexible open-source software for retrosynthetic planning. ChemRxiv. Preprint. https://doi.org/10.26434/chemrxiv.12465371.v1