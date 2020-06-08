---
title: Hosting Jekyll Website on Github
---

## Before Setup

1. Create a Github account

2. Create a new Github repository

3. Install [Git](https://git-scm.com/downloads) on local

For MacOS, the easiest way is to install via homebrew

```
brew install git
```

## Setup Github pages
cd to the website directory and run

```
git init                    #initialize a empty Git on local.
git checkout -b gh-pages    #switch to a new branch gh-pages
git status                  #display all files
```

Then

```
git add .                                 #add the files
git commit -m "initial commit"
```

Here I got the message for Github username

> *** Please tell me who you are.
>
>Run
>
>  git config --global user.email "you@example.com"
>
>  git config --global user.name "Your Name"
>
>to set your account's default identity.

Follow the instruction and put the email address and my name.

```
git config --global user.email "myemail@email.com"
git config --global user.name "myname"
```

After entering, it will ask the password, just type it and press enter.

## Push Files to Github

Copy the git link from Github repository, and run
```
git remote add origin https://github.com/hasturhu/asteroid.git

git push origin gh-pages     #push all files to gh-pages branch
```

It asked me about the username and password on Github. Enter the credentials as instructed.

> Username for 'https://github.com':
>
>Password for 'https://hasturhu@github.com':

As per tutorial, the website should be published now (website link and status is under `Settings` on repository).

Mine got a 404 issue. Not sure why, but I managed to fix it thanks to [Nycen](https://stackoverflow.com/questions/11577147/how-to-fix-http-404-on-github-pages).
```
git commit --allow-empty -m "Trigger rebuild"
```

Tadaa! Now the site is finally on live! I might grab some ice-cream for celebration

:icecream: *★,°*:.☆(￣▽￣)/:*.°★* 。 
Anyways, whenever there's a change on local, run the following code to push update to Github.

```
git add .
git commit -m "some commit messages"
git push origin gh-pages
```
