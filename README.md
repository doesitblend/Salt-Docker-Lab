# Quick Salt Lab
The goal of this project is to create a quick lab for testing and
troubleshooting issues in Salt. The lab should be light weight, but 
allow for testing processes such as upgrades.


## How to use this repository
Use of this repository requires Docker. See the 
[Docker install guide](https://docs.docker.com/engine/install/). 
The repo consists of a bunch of Dockerfiles to build out a master with
several minions on different operating systems. Clone this repo with

```
# git clone https://github.com/doesitblend/Salt-Docker-Lab.git
```
Once downloaded, you can update the compose.yml file with the version
of Salt that you need to install. Then run `docker compose up -d` to 
build the containers locally and run them. The minions should start
and automatically connect to the Salt master. You can then connect to 
the Salt master with `docker exec -it quick-salt-master-1 /bin/bash`.
This will get you on a terminal inside the container where you should
be able to run normal Salt commands. Please keep in mind though that
the daemons are all running under a process manager called Supervisor.
Stopping and starting services will require a command like
```
# supervisorctl status
# supervisorctl stop saltmaster
# supervisorctl start saltmaster
```
The missing `-` is not a typo. The service configuration name in 
Supervisor is referenced this way.

Good luck and feel free to log any issues, or requests for 
functionality.

