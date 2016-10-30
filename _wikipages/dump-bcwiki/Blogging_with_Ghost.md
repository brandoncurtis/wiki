---
title: Blogging with Ghost
permalink: /Blogging_with_Ghost/
---

Deploying Ghost with Forever
----------------------------

<http://support.ghost.org/deploying-ghost/>

    sudo npm install forever -g
    sudo NODE_ENV=production forever start index.js
    sudo forever stop index.js
    sudo forever list

    warn:    --minUptime not set. Defaulting to: 1000ms
    warn:    --spinSleepTime not set. Your script will exit if it does not stay up for at least 1000ms

(these are just warnings, but things seem to work fine)

------------------------------------------------------------------------

extensive setup and hardening: <http://0v.org/installing-ghost-on-ubuntu-nginx-and-mysql/>

Adding Comments
---------------

-   <http://support.ghost.org/add-disqus-to-my-ghost-blog/>
-   <http://ghostforbeginners.com/how-to-enable-comments-on-a-ghost-blog/>
-   <http://ghost.centminmod.com/ghost-posts-with-faster-disqus-load-speed/>
-   <http://ghost.pellegrom.me/adding-disqus-comments-to-ghost/>
-   <http://answers.squarespace.com/questions/5005/how-can-i-add-the-disqus-comment-count-to-a-page>
-   <http://www.allaboutghost.com/how-to-add-disqus-comments-to-ghost/>

<!-- -->

-   <https://disqus.com/admin/universalcode/>
-   <https://help.disqus.com/customer/portal/articles/1454924-ghost-installation-instructions>
-   <https://help.disqus.com/customer/portal/articles/565624-adding-comment-count-links-to-your-home-page>
