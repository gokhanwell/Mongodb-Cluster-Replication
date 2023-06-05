#check volumes and files

        df -h
        lsblk
        sudo file -s /dev/nvme1n1
        
#create new file system for new EBS volume after attach     

        sudo mkfs -t xfs /dev/nvme1n1
        sudo file -s /dev/nvme1n1

#mount path

        sudo mkdir /data
        sudo mount /dev/nvme1n1 /data

#record the fstab file

        sudo lsblk -f  #take the UUID 
        sudo vi /etc/fstab

UUID=2e2f1f7e-7434-45bc-bf8c-bf9112fdd0a1     /data           xfs    defaults,noatime  1   1

        sudo reboot now
