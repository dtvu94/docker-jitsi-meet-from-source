# Jitsi Meet on Docker

Inspiration from <https://github.com/jitsi/docker-jitsi-meet>, I make a tutorial for build from its source code, not from debian packages.

## Target

Assume you have Jitsi-meet components with their sources modification, you intend to build and dockerize them.
Here, this tutorial will guy you how to do it without investigating too much documentations.

There is a sample from <https://github.com/jitsi/docker-jitsi-meet> but they use pre-built packages from debian.
These packages are not suitable to other operating systems.

I will also show a part of my configuration to make it run along with configurations in <https://github.com/jitsi/docker-jitsi-meet>

## Assumptions

Before beginning the guideline, I assume you at least have run all these repository from its source code:

* Jitsi-meet
* Jitsi-videobridege
* Jicofo

There is a guide at <https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-manual>. This guide is not enough since it doesn't have all explanations and configurations. After few time experimenting, I make a guess and conclude them below.

You have to install required dependencies:

* Java JDK 8 (or 11), I run locally with JDK 11, which is fine.
* Maven
* NPM latest version
* Build essential tools
* Devscripts for build deb package of Ubuntu at <https://packages.ubuntu.com/focal/devscripts>

In Dockerfile, I also assume that the process you use to deploy a docker image is as below:

* Build packages from sources by Jenkins (I guide below by commands in terminal)
* Use results to build a docker image

## Project Directory

Main part:
├── jicofo
├── jitsi-meet
├── jitsi-videobridge
├── LICENSE
└── README.md

Each directory:

* jicofo
* jitsi-meet
* jitsi-videobridge

store configuration files, Dockerfile, Makefile.

## Update content of repo

- Go to each directory of above ones, fill in the PROJECT_ROOT with the absolute path of the project clone directory.
- Copy files and folders in each directory into the root folder of each repository.
- Run command

``` bash
make build
```

to build an image with default configuration

### Default configurations

Default configurations and docker-compose.yml file are following the project <https://github.com/jitsi/docker-jitsi-meet>.

If you see their changes and this project is not updated yet, please verify them and use new ones.

### Custom configurations

By experiments, I see that only few configurations required.

Hence, I change a lot. You can compare and figure out some interesting things

## Make and Build
