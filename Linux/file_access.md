Let's go through each command step by step to understand what is happening:

### Initial Command
```bash
[root@rocky Learn]# ls -latr lex
-rw-rw-rwx 1 root root 0 Oct 15 19:28 lex
```
- **`ls -latr`** lists files with detailed information, sorted by time (oldest files at the top).
- The output shows:
  - **`-rw-rw-rwx`**: Permissions of the file `lex`. Initially, the file has:
    - Read (`r`), write (`w`) permissions for the owner (`root`).
    - Read (`r`), write (`w`) permissions for the group (`root`).
    - Read (`r`), write (`w`), and execute (`x`) permissions for others.
  - **`root root`**: The file is owned by the user `root` and the group `root`.
  - **`0`**: The file size is `0` bytes.
  - **`Oct 15 19:28`**: The file was created or modified at this time.

### Command 1
```bash
[root@rocky Learn]# chmod a-rwx lex
```
- **`chmod a-rwx lex`**: This command removes all permissions (read, write, execute) for everyone (user, group, others) from the file `lex`.
- **`a`** stands for "all" (user, group, others), and `-rwx` removes read, write, and execute permissions.

### Checking the File After Command 1
```bash
[root@rocky Learn]# ls -latr lex
---------- 1 root root 0 Oct 15 19:28 lex
```
- Now, the file `lex` has **no permissions** for anyone.
- The **`----------`** shows that there are no read, write, or execute permissions for the owner, group, or others.

### Command 2
```bash
[root@rocky Learn]# chmod a+rwx lex
```
- **`chmod a+rwx lex`**: This command adds read, write, and execute permissions for everyone (user, group, others).
- **`a`** means "all," and `+rwx` grants read, write, and execute permissions.

### Checking the File After Command 2
```bash
[root@rocky Learn]# ls -latr lex
-rwxrwxrwx 1 root root 0 Oct 15 19:28 lex
```
- Now, the file `lex` has **full permissions** for everyone.
- The **`-rwxrwxrwx`** shows that:
  - **User (root)** has read, write, and execute permissions.
  - **Group (root)** has read, write, and execute permissions.
  - **Others** also have read, write, and execute permissions.

### Command 3
```bash
[root@rocky Learn]# chown hulk lex
```
- **`chown hulk lex`**: Changes the ownership of the file `lex` to the user `hulk`.
- Now, `hulk` is the owner of the file instead of `root`.

### Checking the File After Command 3
```bash
[root@rocky Learn]# ls -latr lex
-rwxrwxrwx 1 hulk root 0 Oct 15 19:28 lex
```
- The file is now owned by **`hulk`** (user) and **`root`** (group).
- Permissions remain the same.

### Command 4
```bash
[root@rocky Learn]# chgrp superhero lex
```
- **`chgrp superhero lex`**: Changes the group ownership of the file `lex` to the group `superhero`.
- Now, the group ownership has been updated from `root` to `superhero`.

### Checking the File After Command 4
```bash
[root@rocky Learn]# ls -latr lex
-rwxrwxrwx 1 hulk superhero 0 Oct 15 19:28 lex
```
- The file is now owned by **`hulk`** (user) and **`superhero`** (group).
- Permissions remain the same as before.

### Summary:
1. **`chmod a-rwx lex`** removed all permissions for everyone.
2. **`chmod a+rwx lex`** granted full permissions for everyone.
3. **`chown hulk lex`** changed the file owner to `hulk`.
4. **`chgrp superhero lex`** changed the group ownership to `superhero`.

The commands demonstrate how to control file permissions and ownership on a Linux system.
