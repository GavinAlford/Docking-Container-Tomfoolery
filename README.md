# Docking-Container-Tomfoolery
Used Linode to host kasm on my virtual machine which allowed me to create docker containers that can stream instances of kali Linux, ubuntu, and brave onto my home browser. Used knowledge of linux command line to set up a swap partition in order to install Kasm.

Requirments: 
1.A Lenode account with a running ubuntu 20.02 image
2.Image must have 2vcpus , 4 gigabytes of ra, 50 gigabytes of storage 

Steps:
1.Access your virtual box through your command line 
2.Create a swap partition using the foloowing code

sudo dd if=/dev/zero bs=1M count=1024 of=/mnt/1GiB.swap

3.Change the permissions on the swap partition file

sudo chmod 600 /mnt/1GiB.swap

4.Make the partition into a swap file 

sudo mkswap /mnt/1GiB.swap

5.Activate the swap partition 

sudo swapon /mnt/1GiB.swap

6.Verify that the swap is established 

cat /proc/swaps

7.Make sure the swap will be there upon backup 

echo '/mnt/1GiB.swap swap swap defaults 0 0' | sudo tee -a /etc/fstab

8.Get Kasm 

wget https://kasm-static-content.s3.amazonaws.com/kasm_release_1.10.0.238225.tar.gz

9.Unzip the file 

tar -xf kasm_release*.tar.gz

10.Start the script 

sudo bash kasm_release/install.sh

11.Once the download is done copy the admin credentials you found

12. Go to the ip adress of your lenode 

https:// your lenodes ip

13. Use the admin credintials to log into kasm

There you have it, a personal lab streaming through docker containers that you can open at any time!
