Let's break down what each command and output means in simple terms:

### Command 1:
```bash
[root@rocky ~]# grep babu /etc/shadow
babubutt:!!:20013:0:99999:7:::
```
- The `/etc/shadow` file stores information about user passwords, including password expiration and account settings.
- Running `grep babu /etc/shadow` searches for the user `babubutt` in this file.
- The output explains the following information:
  - **`babubutt`**: The username.
  - **`!!`**: The password is locked or not set up properly.
  - **`20013`**: The last date (in days since 1970-01-01) when the password was last changed.
  - **`0`**: The minimum number of days that must pass before the user can change the password again (currently `0`, so no restriction).
  - **`99999`**: The maximum number of days a password can be used before it expires (set to `99999` days, which means almost never expires).
  - **`7`**: The number of days before the password expires that the user will get a warning.
  - **Other fields (`:::`)**: Empty fields for inactivity period and account expiration.

### Command 2:
```bash
[root@rocky ~]# chage -m 5 -M 90 -W 10 -I 3 -E 8 babubutt
```
- The `chage` command is used to change password aging settings for a user.
- Here’s what each option means:
  - **`-m 5`**: Sets the **minimum** number of days between password changes to `5` days. This means `babubutt` has to wait at least 5 days before changing the password again.
  - **`-M 90`**: Sets the **maximum** number of days that a password can be used before it **expires** to `90` days. After 90 days, `babubutt` must change the password.
  - **`-W 10`**: The user will get a **warning** `10` days before the password expires.
  - **`-I 3`**: Sets the **inactivity** period to `3` days. If `babubutt` doesn't log in within 3 days after the password has expired, the account will be disabled.
  - **`-E 8`**: Sets the **account expiration date** to `8`. Here, `8` means the number of days from the last password change after which the account will expire.

### Command 3:
```bash
[root@rocky ~]# grep babu /etc/shadow
babubutt:!!:20013:5:90:10:3:8:
```
- Running `grep` again shows the updated settings in `/etc/shadow` for `babubutt`:
  - **`5`**: Minimum days before password change.
  - **`90`**: Maximum days a password can be used before it expires.
  - **`10`**: Days before expiry to warn the user.
  - **`3`**: Inactivity period before disabling the account.
  - **`8`**: Account expiration after the password was last changed.

### Summary:
Initially, `babubutt` could change the password anytime, and the password would almost never expire. After running the `chage` command, password aging policies were set, requiring `babubutt` to:
- Change passwords every 90 days.
- Wait at least 5 days between password changes.
- Receive a 10-day warning before the password expires.
- Ensure to log in within 3 days after the password expires; otherwise, the account will be disabled.
- The account will expire 8 days after the last password change.
