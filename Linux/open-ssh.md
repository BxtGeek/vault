### How to manage the passphrase using the alias
```
# create the key
ssh-keygen -t ed25519 -C "Manoj_Key"

# copy the key to the server
ssh-copy-id -i id_ed25519.pub root@192.168.1.85

# need to add the ssha alias into the .bashrc
alias ssha='eval $(ssh-agent) && ssh-add'
source ~/.bashrc

# login into the server
ssh -i ~/.ssh/id_ed25519 root@192.168.1.85  
```
