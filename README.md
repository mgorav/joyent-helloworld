# Joyent's ContainerPilot Pattern Example Using Node.JS Services

## Overview

Autopilot pattern moves all the orchestration responsibilities to the application itself rather than relying on an external orchestrator. **So what is orachestration? Orchestration** is the automation of the operations of an application. Most application require operational tasks like connecting them to related components (joyent-helloworld), and some applications require special attention as they start up or shut down to be sure they bootstrap correctly or persist their data.

**So what is ContainerPilot? ContainerPilot** is added to application’s service. It communicates with the application’s service on one hand and with Consul on the other hand. It takes following key responsibilities:
1. the service registration/discovery within Consul
2. defining how the health check of the service needs to be done
3. defining the dependencies of the current service
4. the management of the service workflow by calling configuration script for preStart / onChange / postStop actions

![Container Piolot](ContainerPilot.jpg)

## Joyent Containers

Before going in the direction of Joyent containerization, let refresh the differences between container vs vm as shown below :

![Container](JoyentContainer.png)


Joyent containers can be categorized into following:

**Option 1.** Infrastructure containers running container-native Linux and SmartOS that work like a typical Unix host.

**Option 2.** Docker containers running Docker images.

**Option 3.** Containers hosting hardware virtual machines running Windows, FreeBSD, or others. These don't offer the same performance advantages, but they offer compatibility for workloads that can't be fully containerized.

For more details & comparision container hosted on different cloud provider refer to [blog](https://www.joyent.com/blog/understanding-triton-containers)

As can be concluded from above, Option 1 & Option 2 are the most high performtant containerization provided by Joyent.

## Application Architecture
The application is divided into 4 parts:

1. **nginx** - nginx server rendering static assets
2. **consul** - service registry & catalog used to keep track of registered services
3. **hello** - Node.js service responding with the word "Hello"
4. **world** - Node.js service responding with the word "World"

Following pictures shows complete architecture diagram:

![HelloWorld](hello-world.png)


![Joyent Arch Diagram](joyent-arch-diagram.jpg)

## Instructions to run

1. `git clone git@github.com:joyent-helloworld.git`
2. `cd hello-world`
3. `docker-compose up -d`
4. `open http://localhost`

![HelloWorld](HelloWorld.png)

The fun part now, this application can be scaled by issuing following command:

`docker-compose scale hello=10 world=6`

## Conclusion
Container pilot is an awsome patten to address loads operation concerns to name the few, rolling restart, graceful shutdown etc implemented as infrastructure as code, handled from within application, rather than some god father orchestrator somewhere - **welcome to the elegant world of "devops", "full stack developer", ...**
