---
title: Holmes Lab Conda
nav_order: 2 
nav_enabled: true 
parent: Amarel Computing
---

# Modules in Holmes Lab Conda
Last updated: May 19, 2025 11:01 AM

## Activate Holmes Lab Conda
In the terminal, signed into Amarel, type:
```bash
conda activate /projects/community/holmesenv
```
Now you are 'in' the Holmes Lab conda environment. Anything you install using `pip install ...` or `conda install ...` will be installed to this conda. 

## Modules in Holmes Lab Conda
To see all the current modules in our conda, type:
```bash
# While already actiated /projects/community/holmesenv
conda list
```

## Add to Holmes Lab Conda
To install packages or modules, just run: 
```bash
pip install packageName
# or
conda install packageName
```

Conda install is safer, but only big / well known packages are available in `conda install`, so pip is also fine. 

## Create your Own Conda based off Holmes Lab Conda
In order to duplicate this environment excute the following:
1. `conda activate MyENV` (where MyENV is the environment name)
2. `conda list --explicit > spec-file.txt`
This will produce `spec-file.txt` that can be used to replicate the environment like this:

3. `conda create --name NewEnv --file spec-file.txt`
4. `conda activate NewEnv`

Now you are inside of your personal conda environment, which is a duplicate of the Holmes Lab environment. If you add packages here, they won't be added to the 

## What is a Conda Environment?
A Conda environment is an isolated workspace that contains a specific set of software packages, libraries, and a Python version — all configured to work together. It allows researchers to run code without worrying about software conflicts or setup differences between computers.

## How We Use Conda in the Holmes Lab
To keep things simple and consistent across the team, we maintain a shared Conda environment that includes all the core packages commonly used in our research (e.g., for data analysis, neuroimaging, statistics, etc.).

Instead of each person manually installing packages on their own system, everyone can activate the Holmes Lab Conda environment and start working immediately with the same setup. This has several key benefits:

- No individual setup required – saves time and reduces setup errors.
- Consistency across users – ensures code runs the same way on everyone’s machine or the HPC cluster.
- Centralized maintenance – when we update or add packages, it only needs to be done once.
- Reproducibility – shared environments make it easier to reproduce results and share notebooks/scripts.


