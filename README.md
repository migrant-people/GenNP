# GenNP
GenNP is a low-threshold and powerful **n**etwork **p**erformance data **gen**erator, with OMNeT++ and INET at its simulation core. It integrates a configuration generation layer, a simulation transformation layer, a result extraction layer, and a result output layer, achieving large-scale random generation of simulation configurations (including networks, traffic, routing protocols, faults, etc.) and multi-granularity extraction of network performance data (such as throughput, drop, delay, jitter, routing table, etc.). Using this tool allows for the easy creation of network performance datasets.
# Parameters
GenNP offers a rich set of parameter configurations. Simply modify the config.py file according to your requirements, and you can generate datasets tailored to your needs.

**1. Smulation configuration**
- Simulation time
- Repetitions number
- Parallelism number
- Temporal granularity
- Throughput, drop, delay, jitter, routing table, etc.)

**2. Network configuration**
- Topology: real network (NSFNET, GBN, GEANT); simulation network (BA, WR, ER )
- Link: bandwidth
- Queue size & scheduling policy: FIFO, DSCP
- Routing protocol: OSPF (helloInterval, routerDeadInterval), RIP (updateInterval, routeExpiryTime)

**3. Traffic configuration**
- Sending configuration (send & stop time, packet size)
- Traffic model (possion, on-off, constant)
- Traffic density, probability of communication between routers

**4. Fault configuration**
- Fault element & number (node, edge, port)
- Fault & Recover time
See the paper for a detailed functional description.

# Getting Started

## Install docker environment and pull GenNP

In order to streamline the installation and deployment process of GenNP, we have encapsulated it within a Docker container. Prior to setting up GenNP, it is imperative that you install a Docker runtime environment on your machine, such as Docker Engine for Linux and Mac or Docker Desktop for Windows, ensuring compatibility and a seamless setup experience.
- Docker Desktop：[https://docs.docker.com/desktop/](https://docs.docker.com/desktop/)
- Docker Engine：[https://docs.docker.com/engine/](https://docs.docker.com/engine/)

After the installation is complete, pull GenNP.

`sudo docker pull migrantdocker/gennp:1.1`

## Run GenNP

**1. Adjust the parameter config.py based on your requirements.**

`sudo docker run -v ./simdatas:/mnt/GenNP/simdatas -it gennp:1.1 /bin/bash`

**2. Enter the directory where GenNP is located.**

`cd /mnt/GenNP`

**3. Run the main program using python3.**

`python3 /mnt/GenNP/main.py`

To avoid occupying excessive memory and computational resources, you can delete the container after each dataset generation using the following command.

**4. Pause all the images.**

`sudo docker stop $(sudo docker ps -a -q)`

**5. Remove all the images.**

`sudo docker rm $(sudo docker ps -a -q)`

# Cite GenNP
