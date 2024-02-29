Sometimes, while deploying the vCenter using a Linux VM, we encounter the following error:

```
"Cannot read properties of undefined (reading 'length')"
```

To resolve this issue, we simply need to install the utility mentioned below:

```
dnf install libnsl
```
