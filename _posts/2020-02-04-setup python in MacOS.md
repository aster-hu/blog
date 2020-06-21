---
title: How to Setup Python in MacOS
---


## Check Current Version of Python

Let's check the current version first:

```python
python --version
#check python2 version

python3 --version
#check python3 version
```

## Update Python3

If you don't have Python installed yet, you can simply downloaded the package from [official website](https://www.python.org).
For me, since I already installed Python, I just upgrade it by [Homebrew](https://brew.sh), which is a great package manager on MacOS.

```shell
brew update
brew upgrade python3
```

Then check the version again
```python
python3 --version
```

Now it should be up-to-date.
