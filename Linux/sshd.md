`sshd` is a **daemon** (a background service) that allows remote connections to your Linux server using the SSH protocol. Below are the steps to install and set up `sshd`.

**Note:** 
- `$` represents a command run by a normal user.
- `#` represents a command run by the root user.

## Step 1: Install OpenSSH Server

Run the following command as `root` to install the OpenSSH server package:

```bash
[root@rocky ~]# yum install openssh-server -y
```

This will download and install the OpenSSH server package. During the process, you'll see information about the package being installed.

**Example Output:**
```
Rocky Linux 9 - BaseOS                                                                                3.6 kB/s | 4.1 kB     00:01    
Dependencies resolved.
Installing:
 openssh-server                     aarch64                     8.7p1-38.el9_4.4                     baseos                     439 k

Transaction Summary
Install  1 Package
...
Installed:
  openssh-server-8.7p1-38.el9_4.4.aarch64                                                                                             

Complete!
```

## Step 2: Enable and Start the SSH Service

After installation, enable and start the SSH service:

### Enable `sshd` (So it starts on boot):
```bash
[root@rocky ~]# systemctl enable sshd
```

### Start `sshd` (To start it immediately):
```bash
[root@rocky ~]# systemctl start sshd
```

### Check the Status of `sshd`:
```bash
[root@rocky ~]# systemctl status sshd
```

**Example Output:**
```
● sshd.service - OpenSSH server daemon
     Loaded: loaded (/usr/lib/systemd/system/sshd.service; enabled; preset: enabled)
     Active: active (running) since Mon 2024-10-21 05:19:38 IST; 4s ago
...
Server listening on 0.0.0.0 port 22.
Server listening on :: port 22.
```

Now, the SSH service is running, and your server is ready to accept SSH connections.

## Step 3: Configure SSH Server (Optional)

You can customize the SSH configuration file located at `/etc/ssh/sshd_config`. Some common configurations include:

- **Set the time interval:**
  ```bash
  ClientAliveInterval 600
  ClientAliveCountMax 0
  ```

- **Disable root login:**
  ```bash
  PermitRootLogin no
  ```
  
- **Allow only specific users to connect:**
  ```bash
  AllowUsers user1 user2
  ```

- **Allow user with the Empty password not to login:**
  ```bash
  PermitEmptyPasswords yes
  ```

- **Set the SSH port:**
  ```bash
  port 22
  ```

After making changes, restart `sshd` to apply them:
```bash
[root@rocky ~]# systemctl restart sshd
```

--- 

That's it! You have successfully installed and configured `sshd` on Rocky Linux.
