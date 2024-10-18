Here's a detailed explanation of each command, along with the output and what it means:

### 1. **`systemctl --version`**
This command checks the version of `systemd` installed on the system. `systemd` is a system and service manager for Linux operating systems. 

**Output Explanation**:
```
systemd 252 (252-32.el9_4.7)
+PAM +AUDIT +SELINUX -APPARMOR +IMA +SMACK +SECCOMP +GCRYPT +GNUTLS +OPENSSL +ACL +BLKID +CURL +ELFUTILS -FIDO2 +IDN2 -IDN -IPTC +KMOD +LIBCRYPTSETUP +LIBFDISK +PCRE2 -PWQUALITY +P11KIT -QRENCODE +TPM2 +BZIP2 +LZ4 +XZ +ZLIB +ZSTD -BPF_FRAMEWORK +XKBCOMMON +UTMP +SYSVINIT default-hierarchy=unified
```
- **systemd 252**: This indicates the version number.
- **+PAM, +SELINUX, etc.**: These are features or libraries supported by `systemd`.
- **default-hierarchy=unified**: Indicates the control group hierarchy in use.

### 2. **`ps -ef | grep -i systemd`**
This command lists all processes running on the system and filters out those related to `systemd`. It helps to see which `systemd` services or processes are currently active.

**Output Explanation**:
```
root         115       1  0 06:17 ?        00:00:00 /usr/lib/systemd/systemd-journald
root         131       1  0 06:17 ?        00:00:00 /usr/lib/systemd/systemd-logind
manojku+     156       1  0 06:17 ?        00:00:00 /usr/lib/systemd/systemd --user
root         201       1  0 06:17 ?        00:00:00 /usr/lib/systemd/systemd --user
```
- Each line represents a `systemd` service or component running on the system.
- **systemd-journald**: Manages system logging.
- **systemd-logind**: Manages user logins and sessions.
- **systemd --user**: Represents user services managed by `systemd`.

### 3. **`systemctl --all`**
This command lists all the units (services, mount points, sockets, etc.) managed by `systemd`, whether they are active or inactive.

**Output Explanation**:
```
  UNIT                                                                LOAD      ACTIVE   SUB       DESCRIPTION                      
  proc-sys-fs-binfmt_misc.automount                                   loaded    active   waiting   Arbitrary Executable File Formats 
  -.mount                                                             loaded    active   mounted   Root Mount
  ...
```
- **UNIT**: The name of the unit.
- **LOAD**: Indicates if the unit's configuration has been loaded.
- **ACTIVE**: The high-level state of the unit (active/inactive).
- **SUB**: More detailed state information.
- **DESCRIPTION**: A brief description of what the unit does.

### 4. **`systemctl status firewalld`**
This command shows the status of the `firewalld` service, including whether it is running or stopped.

**Output Explanation**:
```
● firewalld.service - firewalld - dynamic firewall daemon
     Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; preset: enabled)
     Active: active (running) since Fri 2024-10-18 07:44:52 IST; 6s ago
       Docs: man:firewalld(1)
   Main PID: 1101 (firewalld)
      Tasks: 2 (limit: 16865)
     Memory: 28.4M
        CPU: 214ms
     CGroup: /system.slice/firewalld.service
             └─1101 /usr/bin/python3 -s /usr/sbin/firewalld --nofork --nopid
```
- **Loaded**: Shows if the service is loaded and configured to start.
- **Active**: Indicates if the service is running.
- **Main PID**: The process ID of the `firewalld` service.
- **Tasks, Memory, CPU**: Resource usage details.
- **CGroup**: The control group path where the service runs.

### 5. **`systemctl stop firewalld.service`**
This command stops the `firewalld` service, turning off the firewall.

**Output Explanation**:
```
○ firewalld.service - firewalld - dynamic firewall daemon
     Active: inactive (dead) since Fri 2024-10-18 07:47:08 IST; 1s ago
```
- **Active: inactive (dead)**: Indicates the service is no longer running.

### 6. **`ps -ef | grep firewalld`**
This command checks if the `firewalld` service process is still running. 

**Output Explanation**:
```
root        1135     210  0 07:48 pts/1    00:00:00 grep --color=auto firewalld
```
- Only the `grep` process is shown, indicating `firewalld` is not running.

### 7. **`systemctl start firewalld.service`**
This command starts the `firewalld` service.

**Output Explanation**:
```
● firewalld.service - firewalld - dynamic firewall daemon
     Active: active (running) since Fri 2024-10-18 07:48:30 IST; 9s ago
```
- **Active: active (running)**: Confirms the `firewalld` service has started.

### 8. **`systemctl reload firewalld.service`**
This command reloads the `firewalld` service configuration without stopping the service. This is useful when you make changes to the firewall rules.

**Output Explanation**:
```
● firewalld.service - firewalld - dynamic firewall daemon
     Process: 1169 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCESS)
   Main PID: 1138 (firewalld)
```
- **ExecReload**: Shows the command used to reload the service.
- **status=0/SUCCESS**: Indicates the reload was successful.

### 9. **`systemctl enable firewalld`**
This command configures the `firewalld` service to start automatically at boot time.

**Output**:
No output means the command executed successfully. The service is now set to start automatically when the system boots.

These commands provide a complete set of tools to manage and control services (`daemons`) on a Linux system using `systemd`.
