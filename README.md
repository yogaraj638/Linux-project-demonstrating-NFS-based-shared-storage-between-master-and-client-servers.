# Linux-project-demonstrating-NFS-based-shared-storage-between-master-and-client-servers.
# NFS-Based Shared Storage Architecture

## Project Overview
I configured a master-client setup using Network File System (NFS) to share data across systems without relying on local storage. This project simulates a real-world scenario where multiple clients access a centralized partition hosted on a master server.

## Architecture

**Master Server: 192.168.80.131**
- Shared `/var/oct4_normal` via NFS
- Accessible by all clients

**Client Server: 192.168.80.129**
- Mounted shared partition to `/var/nfs_oct3`
- Accessed files without consuming local disk

## Technologies Used
- OS: RHEL/CentOS
- Services: `nfs`, `rpcbind`
- Configuration: `/etc/exports`
- Port: `2049`
- Package: `nfs-utils`

## What I Did

### On the Master Server
- I installed `nfs-utils` and created a shared directory at `/var/oct4_normal`.
- I configured `/etc/exports` with the rule:  
  `/var/oct4_normal *(rw,sync)`
- I started the required services: `rpcbind` and `nfs`.
- I created sample files using `touch y{1..9}` to simulate shared data.

### On the Client Server
- I installed `nfs-utils` and created a mount point at `/var/nfs_oct3`.
- I mounted the shared directory from the master using:  
  `mount 192.168.80.131:/var/oct4_normal /var/nfs_oct3`
- I verified access by listing the contents of the mounted directory.

## Outcome
- My client server accessed shared data from the master without using any local storage.
- Any changes made on the master were instantly visible on the client.
- This setup demonstrated stateless access to large datasets using NFS.

## Key Learnings
- NFS allows live sharing of data across systems without duplication.
- SCP is for copying files; NFS is for sharing them in real time.
- Proper configuration of exports and permissions is essential for multi-client access.

## Folder Structure
nfs-shared-storage-linux/ ├── README.md ├── configs/ │   └── exports.txt ├── logs/ │   └── client_mount.log ├── screenshots/ │   └── master_ls_output.png │   └── client_ls_output.png



## Author

Yogaraj   
Transitioning into cloud computing  
GitHub:https://github.com/yogaraj638

