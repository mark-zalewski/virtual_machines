# Common VM Config Changes #
## Common packages to install on fresh install
`apt install qemu-guest-agent`

`apt install nfs-common`

`apt install docker.io`

`apt install docker-compose`

## Mounting NFS Shares

1. On the host itself, ensure that nfs-common is installed `apt install nfs-common`
2. Update the fstab file located in /etc to include the NFS shares.  `/etc/fstab`  (See fstab file in repo)

**SSH Keys**

