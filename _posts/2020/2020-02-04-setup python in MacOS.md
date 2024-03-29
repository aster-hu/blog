---
title: How to Setup Python in MacOS
tags: [how-to, python]
---

> **2023 UPDATE: I wrote an [update version of this article](/Setup-python-environment-for-ARM-based-Mac), about setting up python on the new ARM-based Mac for macOS Monterey 12.3 and later.**


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
