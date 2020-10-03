# Devlab docker containers

## Overview

This repo contains a set of base docker images intended to be used to build devlopment environments off of.
Each base image defines a user `devlab` that has their own default home directory under `/home/devlab/` and 
is setup to have sudo access without needing a password, this allows the `devlab` user to perform any needed
tasks that would normaly require root access by using the `sudo` command.

The goal of the `devlab` images are to install the bare minimum to setup a user with sudo access to their
respective container environments which can be used as a base to build more specialized development environments
from.

For example, to build a container that has `nodejs` and `npm` from the `devlab-arch` container you could use
the following docker file:

```docker
FROM devlab-arch

RUN pacman -Syu --noconfirm && pacman --noconfirm -S nodejs npm

ENV TZ="America/Los_Angeles"

RUN ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime.
```

## Usage

To build the images navigate to the directory that the repository was cloned to and run the `docker build` command

```bash
# Example for building the devlab-arch image located in the devlab-arch/ directory.
docker build --rm -t devlab-arch devlab-arch/
```

To run the image as the devlab user and open a bash prompt use the following command:

```bash
docker run --rm -it --user devlab -w /home/devlab --hostname devlab-arch --name devlab-arch devlab-arch bash
```