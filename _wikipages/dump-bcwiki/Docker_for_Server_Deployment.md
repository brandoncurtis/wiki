---
title: Docker for Server Deployment
permalink: /Docker_for_Server_Deployment/
---

Installing Docker
-----------------

    https://docs.docker.com/engine/installation/linux/ubuntulinux/

    sudo apt-get install apt-transport-https ca-certificates
    <already installed>

    sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

    sudo nano /etc/apt/sources.list.d/docker.list
    deb https://apt.dockerproject.org/repo ubuntu-xenial main

    sudo apt update && sudo apt purge lxc-docker
    <purge old stuff>

    apt-cache policy docker-engine
    <check this for correctness>

    sudo apt-get install linux-image-extra-$(uname -r)
    <already installed>

    sudo apt-get update && sudo ap
    sudo apt-get install docker-engine

    sudo service docker start
    sudo docker run hello-world

Install Mattermost with Docker
------------------------------

<http://docs.mattermost.com/install/docker-local-machine.html#one-line-docker-install>

`docker` `run` `--name` `mattermost-preview` `-d` `--publish` `8065:8065` `mattermost/mattermost-preview`