---
layout: default
category: software
permalink: p/virtualenv
featured: true
title: Python Development with Virtual Environments
description: Keep your Python development organized with virtual environments.
image: /images/bc-suit.jpg
author: brandoncurtis
---

Topics to cover:

-   Pip
-   Virtualenv
-   Virtualenvwrapper

(another small change to test the jekyll-feed plugin)

Python Install Python (PIP)
---------------------------

You can use `pip` `freeze` or `pip` `list` to generate a list of the Python packages installed in your current environment. You can [output this list to a file](http://stackoverflow.com/questions/18966564/pip-freeze-vs-pip-list) and use that file to install the exact same packages in another environment.

Virtualenvwrapper
-----------------

<https://virtualenvwrapper.readthedocs.org/en/latest/>

See existing environments—and switch between them—with `workon` (has tab completion).

Make new environments with `mkvirtualenv`.

Once in a virtual environment, [use this to update all Python packages](http://stackoverflow.com/questions/2720014/upgrading-all-packages-with-pip):

`pip` `freeze` `--local` `|` `grep` `-v` `'^\-e'` `|` `cut` `-d` `=` `-f` `1` `|` `xargs` `-n1` `pip` `install` `-U`

-   [Virtualenv with Virtualenvwrapper on Ubuntu (2013)](http://roundhere.net/journal/virtualenv-ubuntu-12-10/)
-   [How To Install virtualenv And virtualenvwrapper In Ubuntu](http://www.unixmen.com/install-virtualenv-virtualenvwrapper-ubuntu/)
-   [virtualenvwrapper in Ubuntu 16.04 (v4.3.1-2)](https://launchpad.net/ubuntu/xenial/+source/virtualenvwrapper)
-   [virtualenvwrapper in pypi (v4.7.1)](https://pypi.python.org/pypi/virtualenvwrapper/)
-   [python-virtualenv in Ubuntu 16.04 (v15.0.1+ds-3)](https://launchpad.net/ubuntu/xenial/+source/python-virtualenv)
-   [python-virtualenv in pypi (v15.0.1)](https://pypi.python.org/pypi/virtualenv)

Development Environment Examples
--------------------------------

All of these examples start from a completely fresh copy of the listed operating system. I create and test these configurations, and do most of my development and troubleshooting work, by cloning a virtual machine running fully-up-to-date Ubuntu 16.04 with the user interface configured exactly how I like it; the cloned VM uses a linked disk tied to the parent VM that only records changes, so I can create a new clean VM to experiment with in just a few seconds and it doesn't take up very much hard drive space.

### Ubuntu 16.04 - Scientific Computing

Prepare the virtual environment tools:

    sudo apt install python-pip
    pip install --upgrade pip
    pip install virtualenvwrapper
    nano ~/.bashrc
    # add this to the end of the file:
      # setup for virtualenvwrapper
      export WORKON_HOME=$HOME/.virtualenvs
      export PATH=$PATH:$HOME/.local/bin
      source /home/brandon/.local/bin/virtualenvwrapper.sh
    source ~/.bashrc

set up a basic virtual environment:

    mkvirtualenv py2sci
    pip install requests[security]
    pip install numpy scipy jupyter

Now we have to install some system-wide stuff so that we can use the various plotting backends in matplotlib. We have to use \`apt install\` instead of \`pip install\` because these things are not Python packages.

Installing wxpython_phoenix should get wx-based backends working:

`pip` `install` `--upgrade` `--trusted-host` `wxpython.org` `--pre` `-f` [`http://wxpython.org/Phoenix/snapshot-builds/`](http://wxpython.org/Phoenix/snapshot-builds/) `wxPython_Phoenix`

[Installing pyside](https://fredrikaverpil.github.io/2015/09/11/installing-pyside-into-a-virtualenv/) should get qt4-based backends working:

`sudo` `apt-get` `install` `build-essential` `cmake` `libqt4-dev` `libxml2-dev` `libxslt1-dev` `python-dev` `qtmobility-dev` `python-pip`

`pip` `install` `pyside`

Installing cairocffi should get cairo-based backends working:

`pip` `install` `cairocffi`

Installing tkinter and the development headers should get tk-based backends working:

`sudo` `apt-get` `install` `python-tk` `tk-dev`

Now you can install matplotlib, either using pip:

`pip` `install` `matplotlib`

or from source pulled from Github:

    sudo apt-get install dvipng
    git clone https://github.com/matplotlib/matplotlib.git
    cd matplotlib
    python setup.py install

If you'd like the gtk3-based backends to work as well, you'll need to install some stuff system-wide; after you've copied it into your virtual environment folder, you can get uninstall it:

    sudo apt install python-gobject python-gi-cairo
    cp -R /usr/lib/python2.7/dist-packages/gi ~/.virtualenvs/mplpip/lib/python2.7/site-packages/
    cp -R /usr/lib/python2.7/dist-packages/glib ~/.virtualenvs/mplpip/lib/python2.7/site-packages/
    cp -R /usr/lib/python2.7/dist-packages/gobject ~/.virtualenvs/mplpip/lib/python2.7/site-packages/
    cp -R /usr/lib/python2.7/dist-packages/gtk-2.0 ~/.virtualenvs/mplpip/lib/python2.7/site-packages/
    cp -R /usr/lib/python2.7/dist-packages/cairo ~/.virtualenvs/mplpip/lib/python2.7/site-packages/
    sudo apt purge python-cairo python-gi python-gi-cairo python-gobject python-gobject-2

Launch Jupyter Notebook with \`jupyter notebook\`. Create a new notebook and check out the available matplotlib plotting backends with <code>%matplotlib -l&lt;?code&gt;; select the one you'd like to use with `%matplotlib` <backend> **before** importing matplotlib's pyplot with `from` `matplotlib` `import` `pyplot` `as` `plt`.

matplotlib is very well-documented; check out [what's new in the latest release](http://matplotlib.org/users/whats_new.html), read more about [how to plot and choose a plotting backend](http://matplotlib.org/faq/usage_faq.html), and see examples of figures in the [matplotlib gallery](http://matplotlib.org/faq/usage_faq.html).

Caltech has [a great intro to Jupyter notebooks](http://bebi103.caltech.edu/2015/tutorials/t0b_intro_to_jupyter_notebooks.html), and you can even download their example notebook and play with it yourself.
