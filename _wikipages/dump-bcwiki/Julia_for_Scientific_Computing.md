---
title: Julia for Scientific Computing
permalink: p/julia-scientific-computing
layout: wikipage
category: software
---

from [|BC| Preparing a virtualenv containing Julia in Jupyter](https://docs.google.com/document/d/13mw6SAP94zFa_jtcaoYqHKwppNv5V3bb1fvpwBQM7Z0/edit#):

    sudo apt-get install python-pip libfreetype6-dev libpng12-dev libffi-dev libssl-dev gfortran tk tk-dev
    pip install virtualenvwrapper
    nano ~/.bashrc

      # configuration for python virtualenvwrapper
      export WORKON_HOME=$HOME/.virtualenvs
      source /home/brandon/.local/bin/virtualenvwrapper.sh
      export PATH="/home/brandon/.local/bin/:$PATH"

    source ~/.bashrc
    mkvirtualenv graveslab
    pip install requests[security]
    pip install numpy scipy matplotlib jupyter pyserial pandas
