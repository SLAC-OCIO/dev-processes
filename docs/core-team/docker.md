SLAC Docker
=====

> Docker is a container management system and is currently the most popular of its kind.  More can be discovered at [docker.com](https://https://www.docker.com/technologies/overview)

## State of Docker at SLAC

Currently, docker is being developed for use with microsites. The Communications org needed hosting of static HTML websites. As there was nothing readily available to meet the needs, and infrastructure would have to be created, provisioned and thought out, I decided to use available resources and go with Docker as a test of sorts.

## The Stack

- Amazon EC2
- Open Stack
- Docker 1.12
- Ansible
- Github
- Jenkins
- Light dusting of bash, until all of the Ansible is finished

## Servers

docker.slac.stanford.edu is on Open Stack and anything needing a domain name is hosted here.  See xalg for access.

rancher.slac.stanford.edu is the Web front end for container/microservice management. It is running Rancher 1.14

ec2-52-36-113-179.us-west-2.compute.amazonaws.com is going to be the Jenkins instance, and run the selenium and code sanity automated tests.


## Code

[**lsst-broc-docker**](https://github.com/SLAC/lsst-broc-docker) The first site to be published in this stack.

[**coms-docker**](https://github.com/SLAC/coms-docker) Ansible playbook - not done yet

[**slac-docker**](https://github.com/SLAC/slac-docker) Central repo for Docker files as I put them together.

> Want in on it?  Want to know more about how this all works? contact @xalg

