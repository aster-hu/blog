---
title: Hosting Jekyll Websiate on Github
---

## Setup

1. Create a Github account

2. Create a new Github repository

3. Install [Git](https://git-scm.com/downloads) on local

For MacOS, the easiest way is to install via homebrew

```
brew install git
```

cd to the website directory and run

```
git init                    #initialize a empty Git on local.
git checkout -b gh-pages    #switch to a new branch gh-pages
git status                  #display all files
```

Run ```git add .``` to add the files

```git commit -m "initial commit"```

> *** Please tell me who you are.
>
>Run
>
>  git config --global user.email "you@example.com"
>  git config --global user.name "Your Name"
>
>to set your account's default identity.

```git remote add origin https://github.com/hasturhu/asteroid.git```

```git push origin gh-pages     ###push all files to gh-pages branch
```

> Username for 'https://github.com':

>Password for 'https://hasturhu@github.com':
