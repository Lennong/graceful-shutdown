This is a bit of shell code to ensure that all Dockers and ProxMox VM's gets gracefully and timely shutdown before the host either reboots or shutdown.
The code is written for a Debian12 host that holds a ProxMox environment with multiple LXC containers and VM's. One of those LXC containers holds a Debian12 which in turn runs a Docker environment.
File access between various containers and VM's are over NFS. This has been a bit problematic as some containers or VM's 'hangs' while trying to unmount NFS before shutdown.

To rectify that this script has been written. 

# Installation:
The script uses the built in standard tools for a Debian 12 installation. To be able to communicate with a container hosted docker environment you also need to install the docker-cli tool.
It can 
You only need the `docker` file, which can be run directly from its location. The script call docker-cli from /usr/bin/docker. Use the commands below to download, unpack and drop it in place: 
```bash
curl https://download.docker.com/linux/static/stable/x86_64/docker-26.0.2.tgz | tar xvz --directory /tmp && mv -v /tmp/docker/docker /usr/bin/docker && chmod +x /usr/bin/docker && rm -rf /tmp/docker
```

# Run commands on remote Docker host with docker-cli 

This is used to connect to another Docker host with docker-cli, without modifying your local Docker installation or when you don't have a local Docker installation.
This script require that you already added an SSH public key to your Docker host for passwordless root access.

# Usage

You can pass one argument to the graceful script that controls the host itself after the Dockers and ProxMox VM's has shut down:

Shutdown host after Dockers and ProxMox VM's
```bash
graceful stop
```
Reboot host after Dockers and ProxMox VM's
```bash
graceful reboot
```
