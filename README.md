# Node.JS Hello World using the Joyent's Autopilot Pattern

1. `git clone git@github.com:joyent-helloworld.git`
2. `cd hello-world`
3. `docker-compose up -d`
4. `open http://localhost`

## Overview

The application is divided into 4 parts:

1. nginx - nginx server rendering static assets
2. consul - service registry & catalog used to keep track of registered services
3. hello - Node.js service responding with the word "Hello"
4. world - Node.js service responding with the word "World"


![Joyent Arch Diagram](joyent-arch-diagram.jpg)
