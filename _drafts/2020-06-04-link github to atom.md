---
title: How to Link and Manage Github Project in Atom
---
Obviously, we need a Github account and project to get start with.

## Setup

#### Project Not in Local

Assuming the project is not in local yet, click `Github` on right corner and choose `Clone an existing Github repository`.

![Screen Shot 2020-06-27 at 1.26.51 AM](https://i.imgur.com/09xzVh8.png)

In the popup window, paste Git link to `Clone from`.

`To directory` is the folder where you want to the project to be cloned into.

![Screen Shot 2020-06-27 at 1.27.04 AM](https://i.imgur.com/Ss0gZFt.png)

After that, it will ask you to click a link to generate a token for authentication. Get the token and paste it, then you should be able to Login.

![Screen Shot 2020-06-27 at 1.23.58 AM](https://i.imgur.com/BxPzhNH.png)

#### Project in Local

It's super easy. Simply go to menu `File` - `Add Project Folder` and choose the parent folder which contains `.git`. Click `Github` on the right corner, it will ask for authentication token just as above. Once it's verified, Atom will recognize it.

## How to Push Request from Local to Github

`Push Request` is a term to describe the changes will be uploaded from local to Github.

After setup, the Git/Github panel will look like below. Any changes we made, the file we changed will change color in tree-view sidebar, and it will also show under `Unstaged Changes` on the right.

![](https://i.imgur.com/g7Mt3zJ.png)

Once we clicked `Stage All`, all files will move to `Staged Changes`.

Now put some comments under `Commit message` and use <kbd>Cmd </kbd> <kbd>Enter </kbd> to confirm. This step is equal to `git commit -m "message"`

![](https://i.imgur.com/4G6n4SX.png)

The comments and `Push` request will be updated. Click `Push` to push the change to Github. It is equal to `git push origin master`

![](https://i.imgur.com/o8A8ues.png)

## How to Pull Request from Github to Local

In contrary to `Push Request`, `Pull Request` means the changes will be downloaded from Github to local folder. To do this, click `Fetch` button on the right corner.
![](https://i.imgur.com/Q2mHYjY.png)

If there's any change available, it will show `Pull x`. Click it to execute `Pull Request`.

[Screen Shot 2020-06-27 at 2.06.52 AM](https://i.imgur.com/yUFaOQB.png)
