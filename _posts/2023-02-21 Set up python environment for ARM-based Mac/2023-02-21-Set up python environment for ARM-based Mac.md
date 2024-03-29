---
title: "Set up a clean python environment for ARM-based Mac in 2023"
tags: [how-to, python]
---

![dan-gold-unsplash](dan-gold-NneNzn0vs44-unsplash.jpg)
*Photo by <a href="https://unsplash.com/@danielcgold?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Dan Gold</a> on <a href="https://unsplash.com/photos/NneNzn0vs44?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>*
  
ARM-based Mac, or Apple Silicon, comes with the powerful M1/M2 chip. Since then, things have changed a lot therefore I'm writing this article to replace [the old blog post](/setup-python-in-macos/) for macOS Monterey 12.3 and later.

## Homebrew: buyer beware

First of all, **I do not recommend using [`brew`](https://brew.sh/) to install python** if you are just starting out. This is a lesson I learned from my early days as a beginner: it is harder to manage the environment in brew, and I still need to use other python package managers such as `pip`, which can get messy very quickly, usually ending up with more than one version in each manager. Unfortunately, this appears at the top of Google search results when  you search "install python on mac", most likely because brew is an all-in-one package manager that also includes other utility packages for macOS.

If you are like me, who just want to have a clean python environment without having to tweak the path here and there, I suggest installing python through [Anaconda](https://www.anaconda.com/products/distribution). Anaconda automatically updates the default python for us, and everything is ready to go. It is also an excellent package manager for installing and updating python packages.

## Which python?

Before OS Monterey, macOS comes with the outdated python 2.7 pre-installed, which doesn't help anybody who are keeping the trend of python 3.

The good news is that, since macOS Monterey 12.3 Apple have removed python 2.7 (finally!) and have the python 3 by default.

We can start by checking the existing python version.

```zsh
% which python
/usr/bin/python3

% python --version
Python 3.9.6
```

As it shows, the default path is `/usr/bin/python3` and it's the python 3 version.

## Step 1: Install Anaconda

Now you may ask why we need to install another python, if macOS already has it pre-installed? The reason is that we need to set up a virtual environment for python, and we also need a package manager to maintain all of our python libraries such as `numpy`.

Anaconda does a great job on this. When we install Anaconda, it also installs python and many popular packages and tools for data science and scientific computing. In short, it basically comes with everything you need to get started with data analysis in python.

Simply download Anaconda on its [official website](https://www.anaconda.com/products/distribution) and choose the version that matches your operating system.

## Step 2: Test the installation

Once Anaconda is installed, it should automatically set the path for us. We can check the python version again in a new Terminal app window. You may need to close the existing Terminal window to ensure it takes effect.

```zsh
% which python
/Users/aster/opt/anaconda3/bin/python
```

We can see that the path is now in the Anaconda folder, which means the default python has been directed to the version within Anaconda.

> *What is the PATH?*

**Good to Know:**  
**PATH** contains the directories of program folder. By setting the path, we are telling the computer to use the right version so that it can execute the code using the version we have specified.

## Step 3: Update or install additional packasges

The packages can be managed in either Anaconda Navigator (an application with GUI), or `conda` in command line. I prefer to use conda because it is faster and easier to manage in bulk.

For example, we can update all python packages to the latest version at once:

```zsh
conda update --all
```

Or install additional packages:

```zsh
conda install name_of_package
```

Now it's done. If you use Jupyter Notebook, you can initiate it by typing `Jupyter notebook` in terminal and start coding python!

## Step 4: Update setting in Visual Studio Code

I use Visual Studio Code as my python IDE and there's few additional steps to ensure we set the current python version in VS Code as well.

The first step is to install the `Jupyter` extension in VS Code so that we can use Jupyter Notebook within VS Code. If we open any Jupyter Notebook files ending with `ipynb`, the application should pop up a message to install the extension.

Once we have the Jupyter extension installed, go to `Settings` and search `python interpreter`, paste the python path from Step 2 to **`Python: Default Interpreter Path`**.

![vsc_setting](vsc_setting.png)

From now on, whenever we run python in VS Code, it will also use the python version in Anaconda to execute the scripts.

## Conda environment

I didn't create a new conda environment because I only use one, which is the `base` environment. However, if you need to switch between environments and play around different versions of python and/or packages, the Anaconda documentation provides detailed tutorials for both [GUI](https://docs.anaconda.com/navigator/tutorials/manage-environments/) and [command line option](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).

## What about other package managers?

Occasionally, you may still encounter some packages that are not available in conda and can only be installed via other managers such as `pip` or `brew`, and that's okay. Pip is supported within conda, and the Anaconda documentation has an article talks about the best practices of [Using Pip in a Conda Environment](https://www.anaconda.com/blog/using-pip-in-a-conda-environment). However it is a relatively advanced topic. For most data analysis job, conda should be enough to satisfy our need.

# Reference

- [Will macOS Big Sur remove the default Python installation for good?](https://apple.stackexchange.com/questions/406244/will-macos-big-sur-remove-the-default-python-installation-for-good)
- [Anaconda Using Pip in a Conda Environment](https://www.anaconda.com/blog/using-pip-in-a-conda-environment)
- [Managing environments — Anaconda documentation](https://docs.anaconda.com/navigator/tutorials/manage-environments/)
- [Managing environments — conda documentation](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)