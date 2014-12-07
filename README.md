Docker Ecosystem Survey
=======================

An incomplete survey of the Docker ecosystem. Comments and pull requests welcome!

Most products mentioned here are in Beta or even Alpha. Competition is fierce and churn is high. Dead products will be removed from the list and new ones will be added.

## Orchestration frameworks (i.e. PaaS software for Docker)

Note: Such a framework should include at least container management, cluster management, and container placement functions. Example optional functions are fault-tolerance, replication, monitoring, development workflow automation, container dependency management, data store services, container versioning, etc.

- Kubernetes: [See archiecture](https://raw.githubusercontent.com/GoogleCloudPlatform/kubernetes/master/docs/architecture.png). 
- [Kubernetes on Mesos](https://github.com/mesosphere/kubernetes-mesos): "Mesos provides the fine-grained resource allocations for pods across nodes in a cluster, and can make Kubernetes play nicely with other frameworks running on the same cluster resources."
- OpenShift: uses Kubernetes
- Mesosphere (Mesos + Marathon + Chronos): Does it support docker dependency and cross-host networking?
- Docker Machine, Swarm, & Compose
- [OpenStack Docker](https://wiki.openstack.org/wiki/Docker)
- SmartDataCenter from Joyent
- Deis from OpDemand: Uses CoreOS (fleet, etcd, etc.). Provides streamlined development/deployment workflow. [Doesn’t support container dependency](https://groups.google.com/forum/#!msg/deis-users/H50Yvh2bMyY/VKPf0DU_q1QJ)
- Flynn: Uses etcd. Similar to Deis. A general PaaS system. Not Docker specific.
- [dokku](https://github.com/progrium/dokku): a mini-Heroku for Docker.
- Serf from maker of Vagrant: not Docker specific. http://www.centurylinklabs.com/decentralizing-docker-how-to-use-serf-with-docker/
- Tsuru: http://blog.tsuru.io/architecture/2014/04/04/running-tsuru-in-production-scaling-and-segregating-docker-containers.html
- [Decking](http://decking.io/)
- Flocker. Mainly designed for data volume management. User specifies container-to-host mapping.

## Host OSes designed for Docker

- [CoreOS](https://coreos.com). Use systemd to manage container upstarts and dependencies, etcd for service discovery, and CoreUpdate for operating system updates.
- [SmartOS](https://www.joyent.com/technology/smartos)

## Host cluster management

- All orchestration frameworks provide cluster management one way or the other
- Docker Machines
- CoreOS Fleet: initd for containers

## Service discovery & configuration

- Consul: comparison to other software: http://www.consul.io/intro/vs
- Kubernetes: No dynamic service discovery yet. [Advocate for static port allocation](http://youtu.be/YrxnVKZeqK8?t=14m31s).
- CoreOS etcd
- ZooKeeper
- doozerd: dead. https://news.ycombinator.com/item?id=6366665
- Serf: decentralized etcd

## Container placement

- Mesosphere Marathon
- CoreOS Fleet: Only for initial placement. Use systemd as underlying tool. Features: X-Fleet:Conflicts, global units, unit multi-instantiation, machine metadata match.
- Docker Swarm
- All orchestration frameworks provide container placement

## Container high-availability & scaling

- Kubernetes ReplicationControllers. [The reconciler model](http://youtu.be/YrxnVKZeqK8?t=20m19s) is great.
- Flynn. The `flynn scale` command
- Deis

## Container dependency management

- CoreOS systemd: ad hoc through unit directives
- fig
- Docker Compose
- Kubernetes Services concept: decouples inter-dependent containers and doesn’t allow explicit dependency declaration
- [Maestro](https://github.com/toscanini/maestro): seems dead. 
- [Maestro NG](https://github.com/signalfuse/maestro-ng)
- Panamax from CenturyLink: Application templating. Have a nice Web UI. “makes deploying complex containerized apps as easy as Drag-and-Drop."

## Container inter-networking

- Kubernetes networking (https://github.com/GoogleCloudPlatform/kubernetes/blob/master/docs/ovs-networking.md)
- systemd in CoreOS: %H specifiers, written to etcd, and use sidekicks to monitor downtimes
- CoreOS Flannel: can be used by Kubernetes: https://github.com/coreos/flannel#flannel
- Weave

Solomon proposed to support VXLAN from the Docker core.

## Container scheduling (i.e. cron for Docker)

- Mesosphere Chronos

## Container updates & versioning

- CoreOS CoreUpdate (paid service): mainly server-side implementations. Client side requires non-trivial integration work (We can use standard docker tag/pull mechanisms instead).
- Fig's Run stage
- Deis: [See this doc](http://docs.deis.io/en/latest/using_deis/config-application/#track-changes)
- Flock?

## Container monitoring & resource enforcement

- Kubernetes cAdvisor
- LMCTFY

## Container data management

- Flocker from clusterHQ. Data volumes follow container location, via ZFS.

## DevOps streamlining & tooling

- Fig
- Deis
- Flynn
- [Modit](https://mod.it): for staging.
- Shippable: for testing & deployment
- docker-cmd: manage docker commands with JSON. https://github.com/iorga-group/docker-cmd. seems dead?

## Image hosting companies (i.e. private registries)

- Quay.io
- Docker Hub Enterprise
- Private Docker registries using the “registry" docker image.

## Container hosting companies

Note: some of them run actual containers on 3rd-party cloud providers.

- AWS
- Rackspace
- GCE
- Orchard
- Tutum
- Joyent
- CoreOS, Managed Linux / Cluster
- https://stackdock.com/

Libraries:
libcontainers
libchan
libswarm (seems dead from github stat as of Dec 2014)

## Useful resources

- [CenturyLink Labs](http://www.centurylinklabs.com/): Covers Docker related news and tutorials.
- [The 12-factor app](http://12factor.net/): Principles of building Docker apps.
- [container42.com](http://container42.com): A Docker blog.
- [The Docker Book](http://www.dockerbook.com/): A book to learn Docker.

## To be surveyed

- Products from [this mind map](http://www.mindmeister.com/389671722/docker-ecosystem).
- [Shipyard](http://shipyard-project.com/)
- Helios
- Centurion
- Shipper
- Flocker
- Panamax from CenturyLink
- [Docker Engine for SmartDataCenter](https://github.com/joyent/sdc-docker)
- OpenStack Docker
- Serf
- Tsuru
- YARN?
- [Decking](http://decking.io/)
- [Project Atomic](http://www.projectatomic.io/) from Redhat. Used by OpenShift. 
- [Geard](http://www.openshift.org/geard/) from Redhat. Core of OpenShift.


## TODOs

- Add more notes to each bullet.
- Add links.


