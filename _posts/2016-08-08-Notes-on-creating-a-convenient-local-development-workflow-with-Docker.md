---
layout: post
title: "Notes on creating a convenient Local Development Workflow with Docker"
date: 2016-08-08 13:31:20
tags:
- workflow
---

While working on a project that requires a new install of PHP and MySql, I came into a halt. It took me a day to re-configure my local development environment.

I then came across Docker. With this research and learning a new technology. My goal is to establish an efficient local development workflow with Docker as I did with creating [Front-End Workflow Theme](https://github.com/rlynjb/frontendflow).

This article [Efficient development workflow using Git submodules and Docker Compose](https://www.airpair.com/docker/posts/efficiant-development-workfow-using-git-submodules-and-docker-compose) gave me a brief overview of what Docker and Git is capable of when architecturing your preferred local development, though, I did have to do further reading on my own to grasp Docker Engine, Docker Compose, and Git submodule (I will not be tackling this topic as I'm focus on Dockerfile and Docker Compose).

-----

### So far, what I know about Docker in regards of hands-on experience is

- we edit or create our source code in a directory from our local machine.
  * to run the app
    * we use Docker to start images we define in **Dockerfile** and `docker-compose.yml` file
- Docker automatically creates a `http://localhost` or `http://0.0.0.0`
- Docker uses Port for each contained apps or websites

-----

### Collections of tutorials

- install **Docker** via its official site [Getting Started with Docker for Mac](https://docs.docker.com/docker-for-mac/)

-----

### Useful commands and info

- Look into **Dockerfile** file references
- Look into `docker-compose.yml` file references and commandline references
- To access a container via terminal:
  * [How to get bash or ssh into a running container in background mode?](http://askubuntu.com/questions/505506/how-to-get-bash-or-ssh-into-a-running-container-in-background-mode)
  * `sudo docker exec -i -t 665b4a1e17b6 /bin/bash #by ID`
  * `sudo docker exec -i -t loving_heisenberg /bin/bash #by Name`
- to start a containter `docker-compose up` or `docker-compose up -d` to detach from status
- to see processes: `docker ps`
- run a command inside container from host
  * `docker exec <container_id> <command>`
-----

### For App sample workflow

- [Practice Workflow with Docker compose](https://docs.docker.com/compose/gettingstarted)

-----

### For CMS sample workflow

- [Practice Workflow with CMS using Docker compose](https://visible.vc/engineering/docker-environment-for-wordpress/)
- **Tip:** you have to be familiar with CMS directory
- We mount local directories from our machine to its Docker container/server with the use of **volume** in its `docker-compose.yml` file
- **Tip:** we can have a copy of CMS install locally on out directory and mount it on Docker container/server
