---
layout: post
title:  "1MinDocker #3 - Fundamental concepts"
date:   2024-10-31T23:00:00+01:00
author: Clelia Bertelli
categories: beginners
---

In [the last article](https://dev.to/astrabert/1mindocker-2-get-docker-kh) we explored how to get Docker for every platform: now, we are very eager to make it to work, but we can't actually do it without having a knowledge of the basic concepts that are behind Docker. In this article we will go through a _minimal glossary_ for Docker:

0. **Virtual machine** (VM): a virtual machine is an isolated environment that manages all its dependencies and required softwares on its own, without relying on the local machine. Once launched, it can be imagined as a separated container which runs independently from the main machine in which it is working. Virtual machines can be local (like the ones we will learn to build and launch with Docker) or on cloud (like Google Cloud, Azure or AWS VMs)
1. **Image**: an image is the base on which we build a separated virtual machine, containing all the instructions and softwares to do so. Even though an image represents nothing but stacked layers of information that contain all the instruction to build the VM, it is not automatically activated: it needs to be booted and then run through the Docker engine. You can think of an image as having collected all the ingredients you need for a cake: they will make one once put together and baked, but they are still definitely not a cake.
2. **Container**: A container is the actual virtual machine in which the image that Docker booted and run is now active. The container's foundations are basically watertight, so there is no possibility of conflicts and/or versioning/platform-specific issues with the local machine, _but_ there is always the possibility for the higher layers of the container to communicate with other containers or to interact with softwares outside of it: this is something that we will see more in details when we will talk about the`compose` plugin. If we imagined an image as a recipe, we can think about a running container as the ingredients put together and being cooked in the oven.
3. **Volume**: A volume is a piece of your local file system that you load to a Docker container when you start running it (so at _runtime_, not at _build time_): sometimes it may happen that you build an image with all the requirements for a specific task, but all the data you need for that task are outside of the running container and, since it is isolated, you cannot access what you need from there. Docker helps you by allowing to map your local file system to the container's file system, without actually flooding the image with extra data that you don't need at _build time_. Let's just say that it is like borrowing a fan from another oven and putting it into the one in which the cake is being cooked, to make it ventilated.
4. **Build**: Building is a core concept for Docker. Building an image means allowing Docker engine to enact all the instructions that are contained into its recipe (the Dockerfile), stocking all the resulting softwares and data inside the image: as we said before, we take all the ingredients and we make them available to be turned into a cake later on. Building can be done locally (on your computer) or on cloud (using Docker Cloud, GitHub Workflows or other services we will talk about in the advanced part of this course). 
5. **Pull and push**: Once the image is built (unless the build was somehow automated/integrated in some other workflow) it is not immediately available to everyone, it needs to be uploaded to an image registry (like Docker Hub or GitHub Container Registry): this action is called `push`. Once an image is made available to the great public, to have it running on our machine we need first to download it, an action called `pull`.
6. **Dockerfile**: As we said before, the Dockerfile is the recipe that contains all the instructions to put together an image. It is a simple text file which is normally called `Dockerfile` (no extensions, generally) that contains a set of keywords (`FROM`, `COPY`, `ADD`, `RUN`, `CMD`, `ENTRYPOINT`... are just some examples) combined with the actual instructions (for instance: `RUN apt update && apt install git` or `COPY . /app/`). A Dockerfile is the base for a build operation, but can be used for more things, like `devcontainers` on Visual Studio Code, `CodeSpaces` on GitHub or `Workspaces` on GitPod (we will see everything in the intermediate part of the series).
We will stop here for this article, but in the next one we will dive deep into the basic commands of Docker CLI, finally getting our hands dirty with some work!🥰