---
layout: default
title: Jekyll for Static Sites
permalink: software/jeckyll
category: software
---

## Building a site with Jekyll

Jonathan McGlone's [Creating and Hosting a Personal Site on GitHub](http://jmcglone.com/guides/github-pages/) is the best guide I've found so far, especially for someone who wants to take a totally custom ground-up approach and not just recycle a template.

The official documentation has [a page on customizing a static site built with Jekyll](https://jekyllrb.com/docs/configuration/) using options in the _config.yml file.  [YAML options can even be nested lists](https://stackoverflow.com/questions/12761152/yaml-front-matter-for-jekyll-and-nested-lists).

Many tutorials discuss how to configure your site as a blog using a _blogpost collection, but [the collections feature is flexible and powerful enough to implement all kinds of site structures](https://jekyllrb.com/docs/collections/).

Liquid tags are the key to fully utilizing Jekyll; they're discussed in-depth in [the Shopify documentation](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) (Shopify is a tool built on Jekyll).


## Gotchas

Avoid [problems with relative links](https://github.com/jekyll/jekyll/issues/332) by using {{ site.baseurl }}{{ post.url }} in Liquid scripts.


## News

In 2016-04, GitHub announced they were [standardized on one Markdown engine, kramdown, for GitHub Pages](https://github.com/blog/2136-a-look-behind-our-decision-to-standardize-on-a-single-markdown-engine-for-github-pages).

## Resources

+ https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/
+ https://jekyllrb.com/docs/github-pages/
+ https://24ways.org/2013/get-started-with-github-pages/
+ https://jekyllrb.com/docs/variables/
+ http://www.remotesynthesis.com/general/2015/10/02/advanced-jekyll-templates/
