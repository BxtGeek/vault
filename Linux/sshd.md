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

To access a remote server without a password using SSH keys, you need to generate an SSH key pair on your local machine and copy the public key to the remote server. Follow these steps:

---

# Access Remote Server Without Password Using SSH Keys

### Step 1: Generate SSH Key Pair on Your Local Machine

Open a terminal on your **local** machine and run:

```bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

- `-t rsa` specifies the type of key to create.
- `-b 4096` sets the key size to 4096 bits (more secure).
- `-C "your_email@example.com"` is an optional comment to help identify the key.

**Example Output:**
```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/youruser/.ssh/id_rsa): 
```

Just press **Enter** to save the key in the default location (`/home/youruser/.ssh/id_rsa`).

**Note:** You can also set a passphrase for extra security or leave it empty for direct access.

### Step 2: Copy the Public Key to the Remote Server

Use the following command to copy your public key to the remote server:

```bash
$ ssh-copy-id user@remote_server_ip
```

Replace `user` with your username on the remote server and `remote_server_ip` with the IP address of the server.

**Example:**
```bash
$ ssh-copy-id john@192.168.1.100
```

**Alternative:** If `ssh-copy-id` is not available, you can manually copy the key:

1. Display the public key:
   ```bash
   $ cat ~/.ssh/id_rsa.pub
   ```

2. Copy the output and paste it into the `~/.ssh/authorized_keys` file on the remote server.

### Step 3: Test SSH Login Without Password

Now, try to connect to the remote server using SSH:

```bash
$ ssh user@remote_server_ip
```

You should be able to connect without being prompted for a password.

**Example:**
```bash
$ ssh john@192.168.1.100
```

### Step 4: Secure Your SSH Configuration (Optional)

For added security, you can disable password authentication on the remote server. Open the SSH configuration file on the **remote server**:

```bash
# vi /etc/ssh/sshd_config
```

Look for the following lines and set them as shown:

```bash
PasswordAuthentication no
ChallengeResponseAuthentication no
```

Then, restart the SSH service:

```bash
# systemctl restart sshd
```

---

Now, your SSH keys are set up, and you can securely access your remote server without a password.
