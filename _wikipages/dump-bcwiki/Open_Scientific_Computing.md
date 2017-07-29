---
title: Open Scientific Computing
permalink: "/Open_Scientific_Computing/"
---

Jupyter
-------

### Kernel: Sage Math

The Sage Jupyter kernel is now available by default in SageMathCloud, along with Sage-6.9 (beta7)

-   <https://www.facebook.com/26593144945/photos/a.350475399945.57169.26593144945/10150572931014946/>
-   <https://twitter.com/sagemath/status/646815293235458048>

Sage Math Cloud updates - 2015-04-08

-   <https://www.facebook.com/permalink.php?story_fbid=10150505231609946&id=26593144945>

Installing the Sage IPython Kernel

-   <http://doc.sagemath.org/html/en/reference/repl/sage/repl/ipython_kernel/install.html>

<!-- -->

    sage: spec.kernel_spec()
    {'argv': ['/opt/sagemath/sage-6.4.1/sage',
      '-python',
      '-m',
      'sage.repl.ipython_kernel',
      '-f',
      '{connection_file}'],
     'display_name': 'Sage 6.9'}