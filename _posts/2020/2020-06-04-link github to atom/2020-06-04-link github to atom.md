---
title: How to Link and Manage Github Project in Atom
tags: [how-to]
---
Obviously, we need a Github account and project to get start with.

## Setup


#### *If Project Not in Local*

Assuming the project is not in local yet, click `Github` on the right corner and choose `Clone an existing Github repository`.

<figure>
<img src = "git1.png" width = "65%" height = "65%" />
<!-- <figcaption>Fig 1. bagian-bagin dari shell prompt.</figcaption> -->
</figure>

There'll be a popup window.

`Clone from`: get Git link from Github page and paste here

`To directory`: it is the folder where you want to the project to be cloned into.

![](git2.png)

After that, it will ask you to click a link to generate a token for authentication. Get the token and paste it, then you should be able to Login.

![](git3.png)

<br>

#### *If Project already in Local*

It's super easy. Simply go to menu `File` - `Add Project Folder` and choose the parent folder which contains `.git`.

Click `Github` on the right corner, it will ask for authentication token just as above. Once it's verified, Atom will recognize it.

## How to Push Request from Local to Github

`Push Request` is a term to describe the changes will be uploaded from local to Github.

After setup, the Git/Github panel will look like below. Any changes we made, the changed files will show under `Unstaged Changes` on the right.

![](push1.png)

Once we clicked `Stage All`, all files will move to `Staged Changes`.

Now put some comments under `Commit message` and click `Commit to Master`(or <kbd>Cmd ⌘</kbd> <kbd>Enter ↵</kbd>) to confirm. This step is equal to `git commit -m "message"`

![](push2.png)

The comments and `Push` request will be updated. Click `Push x` to push the change to Github. It is equal to `git push origin master`.

![](push3.png)

## How to Pull Request from Github to Local

In contrary to `Push Request`, `Pull Request` means the changes will be downloaded from Github to local folder. To do this, click `Fetch` button on the right corner.

![](pull1.png)

If there's any change available, it will show `Pull x`. Click it to execute `Pull Request`.

![](pull2.png)
