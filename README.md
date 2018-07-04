# Docker Selenium

A small prototype running a Selenium Grid inside docker container to parallelize tests.

## Selenium Grid

[Selenium Grid][1] is a way to run tests scenarios against a cluster of browser instances.
Its based on a  master slave architecture. First the hub (master) needs to be started.
Then you can register as many browser instances (nodes) as needed.

## Selenium + Docker

The selenium community provides [a set of standalone and grid Docker images][2]. The
idea behind this prototype is to use `docker-compose` to start a combination of
a Selenium hub instance and multiple browser nodes.

## Usage

Convenience scripts are available inside the `bin` folder.

* `./bin/run <number_of_nodes>` - Starts the hub and instances of Chrome and Firefox (default: 5)
* `./bin/debug <number_of_nodes>` - Starts the hub and instances of debug Chrome and Firefox (default: 5)
* `./bin/stop` - Stops the stack
* `./bin/vnc <container_name>` - Starts the VNC viewer

For anything more complex use `docker-compose` commands

## VNC

It's possible to debug the browsers nodes using VNC.

First you need to determine the port use to connect to the VNC server by
running: `docker port dockerselenium_chrome_<instance_number> 5900`

Then using [a VNC viewer][3] you can connect to the node by using the URL 
`http://127.0.0.1:<port>` and the password `secret`.

## Client connection

Once everything is launched you can access an overview of the nodes cluster at: http://localhost:4444/grid/console.
For more informations on how to run tests on the cluster please take a look
at [the Selenium Grid documentation][4].


[1](https://github.com/SeleniumHQ/selenium/wiki/Grid2)
[2](https://github.com/SeleniumHQ/docker-selenium)
[3](https://www.realvnc.com/en/connect/download/viewer/)
[4](https://github.com/SeleniumHQ/selenium/wiki/Grid2#using-grid-to-run-tests)
