---
title: Setup Must-have Python Libraries for Data Science
---

## Install pip
First of all, we need to install `pip`, a package installer for Python. Follow the instructions [here](https://pip.pypa.io/en/stable/installing/) or run:

```shell
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
```

Then run:

```shell
python3 get-pip.py
#  I'm using `python3` instead of `python` to make sure it direct to Python3
```

## Install Libraries
We just need to install [Seaborn](http://seaborn.pydata.org/installing.html), because it is already incorporated with many other data science libraries such as `pandas` and `numpy`.

```shell
pip install seaborn
```

The dependencies included in Seaborn:
- [numpy](https://numpy.org)
- [scipy](https://www.scipy.org)
- [pandas](http://pandas.pydata.org/)
- [matplotlib](https://matplotlib.org)

Another recommended dependencies is [statsmodels](https://www.statsmodels.org/stable/index.html), which needs to be installed individually.

```shell
pip install statsmodels
```

Additionally, install `ipykernel` in order to run [Hydrogen](https://atom.io/packages/hydrogen) package on Atom.

```shell
python3 -m pip install --user ipykernel
python3 -m ipykernel install --user
```
