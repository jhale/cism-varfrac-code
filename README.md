# FEniCSx examples at CISM 2024

## Introduction

This repository contains source code for the computational examples presented
at the 9th CISM-ECCOMAS Advanced Course on Variational Fracture Mechanics and
Phase-Field Models taking place between July 1st 2014 and July 5th 2024.

The built book can be read at: **INSERT LINK**.

## Installation instructions

The *strongly recommended* approach for installing the software for the course
is using Docker. By using Docker we can ensure that we have a consistent
software environment across all participants. As alternatives, we also provide
instructions for [Google Colab](https://colab.research.google.com) and
[Anaconda](https://www.anaconda.com/download) (`conda`).

### Docker

1. Install Docker Desktop on your system following the instructions
   [here](https://www.docker.com/products/docker-desktop/).

## Authors

- Jack S. Hale, University of Luxembourg.

- Laura de Lorenzis, ETH Zurich.

- Corrado Maurini, Sorbonne Université.

## Developer instructions

### Building

To build this Jupyter book run:

    docker run -v $(pwd):/shared -w /shared -ti --entry-point /bin/bash dolfinx/lab:v0.8.0 
    pip install -r requirements-docs.txt
    jupyter-book build .

and then on the host:

    open _build/html/index.html

On ARM it is necessary to install `pyvista` from a custom binary wheel, see
below.

### Linting and formatting

To lint and format using ruff:

    pip install ruff
    ruff check .
    ruff format .

### Converting .ipynb to .py

This repository stores stores demos in percent-formatted .py files that can
then be converted to e.g. notebooks on demand. To convert legacy notebooks e.g.
`notebook.ipynb` to this format automatically use:

    pip install jupytext
    jupytext --to py notebook.ipynb

which will create a file `notebook.py` which you can then edit with any text
editor. For more information see
[here](https://jupytext.readthedocs.io/en/latest/formats-scripts.html#).

### pyvista on ARM

To install pyvista in ARM docker:

    python3 -m pip install "https://github.com/finsberg/vtk-aarch64/releases/download/vtk-9.2.6-cp310/vtk-9.2.6.dev0-cp310-cp310-linux_aarch64.whl"
    python3 -m pip install pyvista

### Credits

This work includes elements from [Computational fracture mechanics examples
with FEniCSx](https://github.com/newfrac/fenicsx-fracture) under the terms of
the BSD license.

This work includes elements from [NewFrac FEniCSx
training](https://newfrac.gitlab.io/newfrac-fenicsx-training/) under the terms
of the MIT license.
