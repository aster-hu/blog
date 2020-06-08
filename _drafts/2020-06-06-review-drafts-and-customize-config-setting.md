---
title: Drafts and Customize Config Settings
---

## Review Draft Posts
When creating drafts, they are not showing on the site. To review drafts, run the server with draft-enabled.

```
jerkll serve --draft
```

## Customize Front Matters Settings

Add the following default setting in `_config.yml` file.

```
permalink: /:title  # permanent link will be default to title name

#Front matters settings
defaults:
- scope:
    path: ''         # an empty string here means all files in the project
    type: posts      # only posts will be applied with settings
  values:
    layout: post
```

Now be careful when using `Tab` for incident, as it might cause extra space therefore failed the server. (source: [here](https://stackoverflow.com/questions/33066015/jekyll-config-yml-did-not-find-expected-key-while-parsing-a-block-mapping))

Rerun the server.

```
jekyll serve
```
