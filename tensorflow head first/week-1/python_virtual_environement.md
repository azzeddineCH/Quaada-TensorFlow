# Python virtual environement

Created: Feb 18, 2021 10:04 PM
Last Edited Time: Mar 20, 2021 10:51 PM
Status: done
Week: Week 1
presented: Yes

# 1. Why we need a python environement

Python applications will often use packages and modules that don’t come as part of the standard library. Applications will sometimes need a specific version of a library.

This means it may not be possible for one Python installation to meet the requirements of every application. If application A needs version 1.0 of a particular module but application B needs version 2.0, then the requirements are in conflict and installing either version 1.0 or 2.0 will leave one application unable to run.

# 2. for what  python environement is used for

virtualenv is used to manage Python packages for different projects. 

a self-contained directory tree that contains a Python installation for a particular version of Python, plus a number of additional packages. Different applications can then use different virtual environments

![Python%20virtual%20environement%2044e58e256cb74341815b8d72cf76e845/Screen_Shot_2021-02-18_at_23.46.36.png](Python virtual environement 44e58e256cb74341815b8d72cf76e845/Screen_Shot_2021-02-18_at_23.46.36.png)

# 3. CONDA for python Package, dependency and environment management

 

- Conda is an open-source package management system and environment management system that runs on Windows, macOS, and Linux.
- Conda quickly installs, runs, and updates packages and their dependencies.
- Conda easily creates, saves, loads, and switches between environments on your local computer.

# 3. CONDA environment for local usage

```yaml
name:quaada
channels:
    - default
dependencies:
    - python=3.8
    - pip
    - matplotlib
    - jupyterlab
    - pip:
      - tensorflow==2.4.1
      - numpy==1.19.2
      - tensorflow-datasets 4.2.0
```

```bash
conda env create -f environement.yml
```

```bash
conda activate quaada
```