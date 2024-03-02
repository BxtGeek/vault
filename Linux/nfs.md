'''
#install the NFS packages
yum install nfs-utils

#add the below line in the /etc/fstab
192.168.1.73:/mnt/Mainpool/Data	/data	nfs	defaults	0	0

#mount the NFS using the below command 
mount -a
