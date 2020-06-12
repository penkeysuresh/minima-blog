---
layout: post
title:  "Introduction to containers"
date:   2016-10-17 17:04:38 +0530
categories: docker, all
tags: docker
---

In recent times, there is a lot of buzz going on about the containers. Whether it be [Docker](https://www.docker.com/) or [Kubernetes](http://kubernetes.io/) or [OpenVZ](https://openvz.org/Main_Page) or other bunch of upcoming containers, all these containers are working towards solving one of the most fundamental problem developers face in their daily life... not working on server... **but works fine on my local...**

### Need for Containers
Containers are a long overdue items that are much needed and deserved by developers and system administrators, unlike The Dark Knight. Containers provide a self-sufficient environment for a software program to run in terms of OS, runtime, code and file system. 

Since the software is inside this container and not directly on the server, the software becomes independent to the server environment providing a guarantee that the software will work on any other server environment. (A <b>similar</b> abstraction that comes to my mind is a Java program, where the actual compiled code runs on a <b>JVM</b> which needs to be installed on the server, making it compile once and run anywhere, as long as a JVM in installed on the devise). 

This solution will solve two important aspects in Software Development :
- **Consistency** - no more mystery of things not working on a different environment
- **Easy replication** - since things are consistent, it's easier to copy now

As you have guessed by now, a consistent and easily replicable solution will provide the most coveted property for the software **scale**

### What is Docker ?
Docker is one of those containers that is open source, easy to use, and one that is also [very hot](https://github.com/docker/docker/pulse) at the moment. Docker project started about 3 years ago, hit it's major release about year later. Although the technology is very new, it has a very active community and it's updated very frequently. I happened to use it for one of my clients and it did make my life very easy, especially when the entire app had to be shifted from one server to another one.