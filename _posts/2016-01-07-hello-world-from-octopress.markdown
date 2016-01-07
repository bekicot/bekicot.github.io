---
layout: post
title:  "Hello World From Octopress :)"
date:   2016-01-07 13:15:14 +0700
categories: development
---

This blog was build using octopress.

## Installation
Octopress is toolkit for creating blog using jekyll. It included some of the powerfull gem to support creating a blog with jekyll.
Here is how this site is build.

First install bundler if you haven't already.

```
gem install bundler
```

Create Gemfile

```
bundle init
```

and then add octopress to gemfile

```
gem 'octopress', '~> 3.0'
```

And then run `bundle install`

When all of the dependencies has been installed you can preview your blog by running

```
jekyll serve
```

## Configuration
Octopress 3 use the same configuration as the jekyll. Actually it is just a jekyll blog. Octopress only add flavour for easy development. The configuration file is located at `_cofig.yml`

```
vim _config.yml
```

Here is my config.yml looks like

{% highlight yaml %}
# Site settings
title: Yana Agun Siswanto (bekicot)
email: yana.developer@gmail.com 
description: > # this means to ignore newlines until "baseurl:"
  Documenting experience. A blog about Ruby On Rails, Coffeescript, And Javascript Tips. Love Startups and Web Technologies.
baseurl: "" # the subpath of your site, e.g. /blog
url: "bekicot.github.com" # the base hostname & protocol for your site
twitter_username: yana_agun
github_username: bekicot

# Build settings
markdown: kramdown
{% endhighlight yaml %}

## Posting
After all of the installation and configuration stuff, here comes the fun part. Writing a post. To write a post, run :

```
octopress new post 'My Post Name'
```

Open The generated files and edit your post there. But remember, at this point, we are using markdown for editing.

# Next Step
I'm writing this post while learning to craft a blog using jekyll, octopress, and github pages. There might be some error created. If you found one or have suggestion, create an issue at [This blog's repository](http://github.com/bekicot/bekicot.github.com)

Learn More about Octopress

[octopress Github Repository]( http://github.com/octopress/octopress )


Happy Blogging!
