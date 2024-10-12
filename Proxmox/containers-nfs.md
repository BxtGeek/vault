## How to Mount the NFS Share into Containers

1. **Unselect Unprivileged Containers**
   - When creating the containers, make sure to unselect the option for unprivileged containers.

2. **Create the Container**
   - Proceed to create the container as usual.

3. **Log in to Proxmox CLI**
   - Once the container is created, log in to Proxmox using the CLI.

4. **Navigate to the LXC Directory**
   - Navigate to the following directory:
     ```bash
     cd /etc/pve/lxc
     ```

5. **Edit the Container Configuration File**
   - Open the configuration file for the container you just created and add the following line:
     ```bash
     lxc.apparmor.profile: unconfined
     ```
6. **Add these line to the /etc/fstab**
   - To make the NFS mount point permanenet:
     ```bash
     192.168.1.73:/mnt/MainPool /data nfs defaults 0 0
     ```
