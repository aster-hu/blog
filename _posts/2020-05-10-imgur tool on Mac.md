---
title: Imgur Upload Tool for Mac
---

When I'm writing blog, I often need to attach picture URL from Imgur. It becomes extremely annoying to open Imgur each time to upload and copy URL, so I started looking for plugins/tools to make the process easier.

Surprisingly, plugins for Safari and Chrome are all dead because Safari doesn't support unverified plugins anymore, while Chrome's two Imgur extensions are just not working.

[This article](https://help.imgur.com/hc/en-us/articles/209592766-Tools-for-Imgur) lists many other options, however some of them is outdated and not working. Finally I went with [mac2imgur](https://github.com/mileswd/mac2imgur). It's a simple tool that can upload image and also copy the Imgur URL.

*Note: The project is not actively maintained. I tested it in OS Mojave but cannot confirm other OS.*

## Install
Download and install directly from [latest release](https://github.com/mileswd/mac2imgur/releases/tag/b226).

## Usage
Sign in Imgur account first.

![Imgur](/assets/imgur1.png))

Whenever do a screenshot on Mac (<kbd>Cmd⌘</kbd> <kbd>Shift⇧</kbd> <kbd>4</kbd>), it will automatically upload the screenshot to Imgur and copy image URL to clipboard.

![Imgur](/assets/imgur2.png)

If you need to upload a picture other than screenshot, simply drag the image to the menu bar icon, and it will do the work.

After uploading, I can easily paste the URL in my markdown file like this.

```
![Imgur]https://i.imgur.com/KavpJsA.png
```

Simply and easy. I highly recommend it to anyone who's using Imgur as their image source.
