---
title: How to Sync Atom Packages Between Devices
tags: [how-to]
---

Atom itself doesn't provide cloud syncing. Lucky, there're other options out there can provide sync support.

I'm using [Sync-settings](https://atom.io/packages/sync-settings), which can synchronize both packages and settings.

## Install

Sync-settings package need to be installed in both devices.

Simply search `sync-settings` in Atom packages or install via [package link](https://atom.io/packages/sync-settings).

## Create Personal Access Token and Configure

This should be done on the device to be backed up.

1. Create a [personal access token](https://github.com/settings/tokens/new?scopes=gist).
2. In the settings, we only need to tick permission `Gist: create gists`.
3. Copy the generated `personal access token`
4. Paste to sync-settings configuration under `Personal Access Token`

## Create a Gist and Configure
Same as above, do it on the device that needs to be backed up

1. Create a new [gist](https://gist.github.com/)
  - Leave description empty
  - Use `packages.json` in "Filename including extension..."
  - Type anything on the body
2. Save the gist and copy the generated `gist id`.
3. Paste `gist id` in sync-settings configuration under `Gist ID`

## Create Backup

On the same device, use <kbd>Cmd⌘</kbd> <kbd>Shift⇧</kbd> <kbd>P</kbd> to open Atom Command Palette.

In the pop up window, enter `sync-settings` and choose `sync-settings: backup`. There should be a window notifying that the backup has been created.

## Restore from Backup
Now we need to get the same `gist id` and paste to the second device.

1. On the second device, go to [gist.github.com](https://gist.github.com).
2. Click "See all of your gists" on top right corner. The gist we created is saved in here
3. Open the gist, copy the last part of url after the username
> https://gist.github.com/username/this-part-is-gist-id
4. Paste the `gist id` in sync-settings configuration under `Gist ID`
5. <kbd>Cmd⌘</kbd> <kbd>Shift⇧</kbd> <kbd>P</kbd> to open Atom Command Palette, and enter `sync-settings: restore`

Now just grab a coffee and wait until Atom finish installing all packages. The settings and packages have been synced between two devices.
