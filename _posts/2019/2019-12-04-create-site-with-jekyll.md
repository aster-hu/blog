---
title: Create a Site by Using Jekyll
tags: [how-to]
---

## Install Jekyll

I followed this [guide](https://jekyllrb.com/docs/installation/macos/) along with Giraffe Academy's [video tutorial](https://youtu.be/WhrU9m82Wm8) to install the local environment on MacOS Mojave.

In the last step where I checked jekyll version `jekyll -v` , I got some error messages:

> `check_for_activated_spec!': You have already activated public_suffix 4.0.5, but your Gemfile requires public_suffix 4.0.1.
>
> Prepending `bundle exec` to your command may solve this. (Gem::LoadError)

After some research, it was resolved by updating some old dependencies (source: [#6227](https://github.com/jekyll/jekyll/issues/6227)).

```ruby
bundle update
```

## Create a Site

Giraffe Academy's [video series](https://youtu.be/pxua_1vyFck) is really helpful and he would also briefly explained how it works from structure layer.

1. Create site server:
```ruby
jekyll new Sitename
```
2. Direct to the site directory (*sitename* is also the name of the root folder).
```shell
cd sitename/
```
3. Run server:
```ruby
bundle exec jekyll serve
```

In this step, I got the error below:

> Could not find gem 'minima (~> 2.5)' in any of the gem sources listed in your Gemfile.
>
> Run `bundle install` to install missing gems.

The message is quite straightforward so I just followed the instruction and run

```ruby
bundle install
```

Every time when we need to re-run the server, repeat step 2-3.

## Review Draft Posts
When creating drafts in `/_drafts` folder, they are not showing on the site. To review drafts, run the server with draft-enabled.

```ruby
jekyll serve --drafts
```

## Front Matters Settings

Front Matters Settings are the pre-determined settings that applies to all or some of the posts. I added the following default settings in `_config.yml` file.

```yaml
permalink: /:title  # permanent link will be default to title name

#Front matters settings
defaults:
- scope:
    path: ''         # an empty string here means all files in the project
    type: posts      # only posts will be applied with these settings
  values:
    layout: post
```

Now be careful when using <kbd>Tab ⇥</kbd> for incident, as it might cause extra space therefore failed the server. (source: [here](https://stackoverflow.com/questions/33066015/jekyll-config-yml-did-not-find-expected-key-while-parsing-a-block-mapping))

Rerun the server.

```ruby
bundle exec jekyll serve
```
