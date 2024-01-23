# Common VM Config Changes #
## Common packages to install on fresh install
`apt install qemu-guest-agent`

`apt install nfs-common`
## Mounting NFS Shares

1. On the host itself, ensure that nfs-common is installed `apt install nfs-common`
2. Update the fstab file located in /etc to include the NFS shares.  `/etc/fstab`  (See fstab file in repo)

**SSH Keys**

## How to create tar backup file?

To create a tar backup file, first identify the files and folders that would be part of your backup. Let’s assume we want to take backup of /home/linuxtechi, /etc and /opt folder. Run following tar command,

$ tar <options>  {tar-backup-filename}  {files-folders-to-be-backed-up}

`$ sudo tar -cvpf  system-back.tar  /home/linuxtechi /etc /opt`

This will create a tar ball in the present working directory. In above tar command, we have used following options

* c – Create new archive
* v – display verbose output while creating tar file
* f – archive file name
* p – preserve permissions

As you have seen that we have not used any compression options to compress tar file. So, to compress the tar backup file during the archive use -z ( gzip compression) or -j (bzip2 compression)

**Creating tar backup along with gzip compression**

Use ‘z’ in tar command to use gzip compression. This time tar backup file will have extension either .tgz or .tar.gz

`$ sudo tar -zcvpf system-back.tgz /home/linuxtechi /etc /opt`

**Creating tar backup along with bzip compression**

Use ‘j’ option in tar command to use bzip2 compression, this time tar backup file will have extension either .tbz2 or .tar.bz2

`$ sudo tar -jcvpf system-back.tbz2 /home/linuxtechi /etc /opt`

**How to exclude file while creating tar backup?**

To exclude a file while creating tar backup, use ‘-X’ option followed by the exclude file. To use exclude feature we must create a exclude file which will have file name to be excluded.

`$ cat exclude.txt`

`/etc/debconf.conf`

`/etc/hosts`

`$ `

Run following command to exclude files mentioned in exclude.txt while creating tar backup of /etc


`$ sudo tar -X exclude.txt -zcpvf etc-backup.tgz /etc`

**How to view the contents of tar backup?**

To view the contents of tar backup, use ‘-t’ option, complete options would be ‘-tvf’. Example is shown below:

`$ sudo tar -tvf system-back.tgz | grep -i etc/fstab`

`-rw-rw-r-- root/root    665 2021-07-07 04:57 etc/fstab`

`$`

**How to extract tar backup?**

Use ‘-x’ option in tar command to extract tar backup, complete option would be ‘-xpvf’. Example is shown below

`$ sudo tar -xpvf system-back.tgz`

This command will extract system-back.tgz in the current working directory. In case you want extract it in a particular folder then use ‘-C’ option followed by the folder path. In the following example we are extracting system-back.tgz in /var/tmp folder.

`$ sudo tar -xpvf system-back.tgz -C /var/tmp/`

`$ ls -l /var/tmp/`

## Tools
