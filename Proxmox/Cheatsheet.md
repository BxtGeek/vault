# Proxmox Cheatsheet

This page presents a list of commonly used commands for Proxmox.

**Categories:** cheatsheet, proxmox

Access this page by simply typing in "cs proxmox" in your browser address bar if you have bunnylol configured.

## Commands

### VM Management

#### Basics

- List VMs: `qm list`
- Create or restore a virtual machine: `qm create <vmid>`
- Create or restore a virtual machine with core, memory, disks specified: `qm create <vmid> --name <vm-name> --cores <number-of-cores> --memory <memory-size-in-bytes> --scsi0 file=<vg-name>:<size-in-gb> --cdrom local:<iso-name> --net0 virtio,bridge=<bridge-name>`
- Start a VM: `qm start <vmid>`
- Suspend virtual machine: `qm suspend <vmid>`
- Shutdown a VM: `qm shutdown <vmid>`
- Reboot a VM: `qm reboot <vmid>`
- Reset a VM: `qm reset <vmid>`
- Stop a VM: `qm stop <vmid>`
- Destroy the VM and all used/owned volumes. Removes any VM specific permissions and firewall rules: `qm destroy <vmid>`
- Enter Qemu Monitor interface: `qm monitor <vmid>`
- Get the virtual machine configuration with both current and pending values: `qm pending <vmid>`
- Send key event to virtual machine: `qm sendkey <vmid> <key> [OPTIONS]`
- Show command line which is used to start the VM (debug info): `qm showcmd <vmid> [OPTIONS]`
- Unlock the VM: `qm unlock <vmid>`
- Clone a VM: `qm clone <vmid> <newid>`
- Clone a VM in full clone mode and also set the name: `qm clone <vmid> <newid> --full --name <name>`
- Migrate a VM: `qm migrate <vmid> <target-node>`
- Show VM status: `qm status <vmid>`
- Clean up resources for a VM: `qm cleanup <vmid> <clean-shutdown> <guest-requested>`
- Create a Template: `qm template <vmid> [OPTIONS]`
- Set virtual machine options (synchronous API): `qm set <vmid> [OPTIONS]`

#### Cloudinit

- Get automatically generated cloudinit config: `qm cloudinit dump <vmid> <type>`
- Get the cloudinit configuration with both current and pending values: `qm cloudinit pending <vmid>`

#### Disk

- Import an external disk image as an unused disk in a VM: `qm disk import <vmid> <source> <storage>`
- Move volume to different storage or to a different VM: `qm disk move <vmid> <disk> [<storage>] [OPTIONS]`
- Rescan all storages and update disk sizes and unused disk images: `qm disk rescan [OPTIONS]`
- Extend volume size: `qm disk resize <vmid> <disk> <size> [OPTIONS]`
- Unlink/delete disk images: `qm disk unlink <vmid> --idlist <string> [OPTIONS]`
- Rescan volumes: `qm rescan`

#### Snapshot

- List all snapshots: `qm listsnapshot <vmid>`
- Snapshot a VM: `qm snapshot <vmid> <snapname>`
- Delete a snapshot: `qm delsnapshot <vmid> <snapname>`
- Rollback a snapshot: `qm rollback <vmid> <snapname>`
- Open a terminal using a serial device (The VM needs to have a serial device configured, for example serial0: socket): `qm terminal <vmid> [OPTIONS]`
- Proxy VM VNC traffic to stdin/stdout: `qm vncproxy <vmid>`

### Others

- Execute Qemu Guest Agent commands: `qm guest cmd <vmid> <command>`
- Execute the given command via the guest agent: `qm guest exec <vmid> [<extra-args>] [OPTIONS]`
- Get the status of the given pid started by the guest-agent: `qm guest exec-status <vmid> <pid>`
- Sets the password for the given user to the given password: `qm guest passwd <vmid> <username> [OPTIONS]`

### PV, VG & LV Management

- Create a PV: `pvcreate <disk-device-name>`
- Remove a PV: `pvremove <disk-device-name>`
- List all PVs: `pvs`
- Create a VG: `vgcreate <vg-name> <disk-device-name>`
- Remove a VG: `vgremove <vg-name>`
- List all VGs: `vgs`
- Create a LV: `lvcreate -L <lv-size> -n <lv-name> <vg-name>`
- Remove a LV: `lvremove <vg-name>/<lv-name>`
- List all LVs: `lvs`

### Storage Management

- Create a new storage: `pvesm add <type> <storage> [OPTIONS]`
- Allocate disk images: `pvesm alloc <storage> <vmid> <filename> <size> [OPTIONS]`
- Delete volume: `pvesm free <volume> [OPTIONS]`
- Delete storage configuration: `pvesm remove <storage>`
- List storage content: `pvesm list <storage> [OPTIONS]`
- An alias for pvesm scan lvm: `pvesm lvmscan`
- An alias for pvesm scan lvmthin: `pvesm lvmthinscan`
- List local LVM volume groups: `pvesm scan lvm`
- List local LVM Thin Pools: `pvesm scan lvmthin <vg>`
- Get status for all datastores: `pvesm status [OPTIONS]`

### Template Management

- List all templates: `pveam available`
- List all templates: `pveam list <storage>`
- Download appliance templates: `pveam download <storage> <template>`
- Remove a template: `pveam remove <template-path>`
- Update Container Template Database: `pveam update`

### Container Management

#### Basics

- List containers: `pct list`
- Create or restore a container: `pct create <vmid> <ostemplate> [OPTIONS]`
- Start the container: `pct start <vmid> [OPTIONS]`
- Create a container clone/copy: `pct clone <vmid> <newid> [OPTIONS]`
- Suspend the container. This is experimental: `pct suspend <vmid>`
- Resume the container: `pct resume <vmid>`
- Stop the container. This will abruptly stop all processes running in the container: `pct stop <vmid> [OPTIONS]`
- Shutdown the container. This will trigger a clean shutdown of the container, see lxc-stop(1) for details: `pct shutdown <vmid> [OPTIONS]`
- Destroy the container (also delete all uses files): `pct destroy <vmid> [OPTIONS]`
- Show CT status: `pct status <vmid> [OPTIONS]
