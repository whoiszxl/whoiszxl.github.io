# The Jekyll Template for Cotes' Blog

[![Build Status](https://travis-ci.org/cotes2020/cotes-blog.svg?branch=master)](https://travis-ci.org/cotes2020/cotes-blog)
[![GitHub release](https://img.shields.io/github/release/cotes2020/cotes-blog.svg)](https://github.com/cotes2020/cotes-blog/releases)
[![GitHub license](https://img.shields.io/github/license/cotes2020/cotes-blog.svg)](https://github.com/cotes2020/cotes-blog/blob/master/LICENSE)
[![996.icu](https://img.shields.io/badge/link-996.icu-red.svg)](https://996.icu)

My personal Jekyll blog, please check the deployment: [https://blog.cotes.info](https://blog.cotes.info).

## Configuration

Check files in `_data/`:

* meta.yml
* profile.yml
* settins.yml

Override the fields inside to your own.


## Writing

There are few things you should know about writing a post.

### Table of Contents

By default, the table of contents (TOC) is displayed on the right panel of the post. If you want to turn it off globally, go to `_data/settings.yml` and set `toc` to `false`. If you want to turn off TOC in a separate post, then add the following to post's [Front Matter](https://jekyllrb.com/docs/front-matter/):

```yaml
---
toc: false
---
```


### Comments

Similar to TOC, the [Disqus](https://disqus.com/) comments is loaded by default for each post, and the global switch is defined in `comments` of `_data/settings.yml` . If you want to close the comment module of a post separately, add the following to the **Front Matter** of the post:

```yaml
---
comments: false
---
```


### Categories and Tags

The pages for all posts' categories and tags are placed in the `categoreis/` and `tags/` respectively.

Let's say there is a post with title `The Beautify Rose`, it's Front Matter as follow:

```yaml
---
title: "The Beautify Rose"
categories: [Plant]
tags: [flower]

 ...

---
```

> Note: `categories` has at most two elements.

Now you need to create two files for `categories` and `tags`:

1. Create **Category** file `categories/Plant.html` and fill:

```yaml
---
layout: category
title: Plant        # The title of category page.
category: Plant     # The category name in post
---
```

2. Create **Tag** file `tags/flower.html` and fill:

```yaml
---
layout: tag
title: Flower       # The title of tag page.
tag: flower         # The tag name in post.
---
```

If you find this to be time consuming, please use the script tool `pages_generator.py` that placed in `_scripts/tools/`.

The python script needs [ruamel.yaml](https://pypi.org/project/ruamel.yaml/), make sure it's installed in your environment. Now run the tool:

```bash
python _scripts/tools/pages_generator.py
```

Few seconds later, it will create the Categoreis and Tags HTML files automatically.

## Deployment

First run requires the following command:

```bash
bundle install
```

`bundle` will install all plugins declared in `Gemfile` automatically.

### Local

```bash
bundle exec jekyll serve
```

Open your brower and visit: [http://127.0.0.1:4000](http://127.0.0.1:4000)

### GitHub Pages

Step 1. Build project locally and store output to `docs` in root directory:

```bash
bundle exec jekyll build JEKYLL_ENV=production -d docs
```

Step 2. Git commit and push the changes of `/docs` to remote repository.

Step 3. [Publishing your GitHub Pages site from a /docs folder on your master branch
](https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages#publishing-your-github-pages-site-from-a-docs-folder-on-your-master-branch).
