# Swap-Space
Swap space in Linux is used when the amount of physical memory (RAM) is full. If the system needs more memory resources and the RAM is full, inactive pages in memory are moved to the swap space. While swap space can help machines with a small amount of RAM, it should not be considered a replacement for more RAM. Swap space is located on hard drives, which have a slower access time than physical memory. Swap space can be a dedicated swap partition (recommended), a swap file, or a combination of swap partitions and swap files. 

0. To show swap Space command:

        swapon --show
2. Check the Current Swap Usage: You can check your current swap usage by using the free command

        free -h
3. List the Existing Swap Space: You can see the existing swap partitions and files by using the swapon command

        swapon -s
4. Create a Swap File (if needed): If you don't have a swap file or want to create a new one, you can use the command to create a swap file of the desired size. Replace <size> with the size you want (e.g., 1G for 1 gigabyte):

        sudo fallocate -l <size> /swapfile
5. Set the correct permissions on the swap file:

        sudo chmod 600 /swapfile
6. Then, initialize the swap file:
   
        sudo mkswap /swapfile
7. Activate the swap file:

        sudo swapon /swapfile
8. Make the swap space persistent:Open the fstab file:

       sudo vi /etc/fstab
9. Add the following line at the end of the file:
   
       /swapfile none swap sw 0 0

10. If you want to disable swap temporarily, you can use the swapoff command:

        sudo swapoff -a
11. Regenerate mount units so that your system registers the new configuration:

        systemctl daemon-reload
   
