This is a bit of shell code to ensure that all Dockers and ProxMox VM's gets gracefully and timely shutdown before the host either reboots or shutdown.
The code is written for a Debian12 host that holds a ProxMox environment with multiple LXC containers and VM's. One of those LXC containers holds a Debian12 which in turn runs a Docker environment.
File access between various containers and VM's are over NFS. This has been a bit problematic as some containers or VM's 'hangs' while trying to unmount NFS before shutdown.

To rectify that this script has been written. 

Installation:
