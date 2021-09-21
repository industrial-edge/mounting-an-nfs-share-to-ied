# Mounting an NFS share to IED

- [Mounting an NFS share to IED](#mounting-an-nfs-share-to-ied)
  - [Description](#description)
    - [Overview](#overview)
    - [General Task](#general-task)
  - [Requirements](#requirements)
    - [Used components](#used-components)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Documentation](#documentation)
  - [Contribution](#contribution)
  - [Licence and Legal Information](#licence-and-legal-information)

## Description

### Overview

This is a tutorial on how to connect an NFS shared folder located on a server to a Industrial Edge Device and use it as a volume for Docker container.

Network File System (NFS) is a file system protocol allowing a user on a client computer to access files over a network like a local storage.

This application example uses OpenSSH-server image made by LinuxServer.io. More info can be found at the following website: [OpenSSH-server website](https://hub.docker.com/r/linuxserver/openssh-server).

### General Task

![Network topology](docs/graphics/nfs_network.png)

The client is connected through SSH in Terminal to the OpenSSH-server container running on Industrial Edge Device. The server shares an NFS folder with Industrial Edge Device and the OpenSSH-server container uses this folder as a volume.

## Requirements

### Used components

- Docker Engine 18.09.6
- Docker-compose 1.25.0
- Ubuntu Server
  - nfs-kernel-server package

## Installation

A step by step installation guide can be found in the [docs](docs/installation.md)

## Usage

After installing the app to Industrial Edge Device, you should be able to SSH to the OpenSSH-server container to test that everything works correctly.

        ssh edge@192.168.178.20 -p 45555
        password: edge

In the following pictures we can see a conversation between a server and a client. The client is connected through a terminal to a container running on an Industrial Edge Device that is using an NFS share as a volume. On the server, we create a new file called *hello.txt* and write "Hello, IED!" into it. We then read the file on the client computer and see the sentence has been succesfully saved on the server and the changes to the file were sent to the client. After that we write "Hello, Server!" on the client computer into the same *hello.txt* file. As we can see on the server computer, the changes were registered and the file on the server side now containes "Hello, Server!" message sent by the client.

![client](docs/graphics/hello1.png)

![server](docs/graphics/hello2.png)

## Documentation

- You can find further documentation and help in the following links
  - [Industrial Edge Hub](https://iehub.eu1.edge.siemens.cloud/#/documentation)
  - [Industrial Edge Forum](https://www.siemens.com/industrial-edge-forum)
  - [Industrial Edge Landing page](http://siemens.com/industrial-edge)

## Contribution

Thank you for your interest in contributing. Anybody is free to report bugs, unclear documentation, and other problems regarding this repository in the Issues section. Everybody is free to propose any changes to this repository using Pull Requests.

## Licence and Legal Information

Please read the [Legal information](LICENSE.md).
