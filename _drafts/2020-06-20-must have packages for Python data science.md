

## Install pip
https://pip.pypa.io/en/stable/installing/

```shell
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
```

Note that I'm using `python3` instead of `python` because it will direct `pip` under Python3

```shell
python3 get-pip.py
```

Install Seaborn
http://seaborn.pydata.org/installing.html

```shell
pip install seaborn
```

#### Install Dependencies for Seaborn

[numpy](https://numpy.org)
[scipy](https://www.scipy.org)
[pandas](http://pandas.pydata.org/)
[matplotlib](https://matplotlib.org)

*Recommended dependencies*
[statsmodels](https://www.statsmodels.org/stable/index.html)


```shell
python3 -m pip install --user numpy scipy matplotlib pandas statsmodels

#additionally, install ipykernel for Hydrogen
python3 -m pip install --user ipykernel
python3 -m ipykernel install --user
```

## Install [Jupyter Notebook](https://jupyter.org/index.html)

Jupyter Notebook is a web-based application that allows you to create and share documents that contain live code, equations, visualizations and narrative text.

```shell
pip install notebook
```

To run the notebook:
```shell
jupyter notebook
```

## Plugins for Hydrogen

https://nteract.gitbooks.io/hydrogen/#plugins-for-hydrogen
