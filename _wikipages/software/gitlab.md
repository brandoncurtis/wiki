---
layout: default
title: GitLab Version Control Manager
permalink: software/gitlab
category: software
---

GitLab Version Control Manager
==============================

Your own personal GitHub-in-a-box!

Configuration
-------------

### Disabling superscript

[MathJax feature request on GitLab](https://gitlab.com/gitlab-org/gitlab-ce/issues/13690)

[How To Add MathJax rendering support to GitLab](https://redroom.me/gitlab-mathjax.html)

[Another how-to on integrating MathJax with GitLab](http://nd.psychstat.org/blog/integrate_mathjax_with_gitlab)

After configuring, making sure to restart GitLab with `sudo gitlab-ctl restart`.

The above link claims:

>By default, gitlab has the (annoying) feature of using carrot as a superscript. This breaks mathjax for ever equation with a superscript, so to turn it off in the file app/helpers/gitlab_markdown_helper.rb. Simply set superscript to false.

However, there is no mention of superscripting in this file:

`gitlab/embedded/service/gitlab-rails/app/helpers/gitlab_markdown_helper.rb`

or in the [GitLab Flavored Markdown Reference](https://github.com/gitlabhq/gitlabhq/blob/master/doc/user/markdown.md)

...but it DOES end up causing problems!  You do have to turn off subscripting, but now Redcarpet (Ruby Markdown parser) is called through Banzai and the edits must be made here:
 `gitlab/embedded/service/gitlab-rails/lib/banzai/filter/markdown_filter.rb`

[More discussions of LaTeX support on GitLab, including pitches for KaTeX](https://gitlab.com/gitlab-org/gitlab-ce/issues/13180)
