README


** January 12th, 2022 **

This script still works in a new proxmox environment.  If there are issues you have please opne an issue and I will look into it.  Also make sure you have snippets setup becuase that appears to be a common issue when running the script, so make snippets are setup in proxmox or issues will arise.  I will look into updating the cloud images avaiable.

So I had to update to remove autostart after creation, because it was creating issues with the custom cloud-init from the script.  I don't know why but I am looking into it.  Now after creating the VM you should just be able to click start and after boot up and all that your custom values from the script should be usuable like the username and password.

*****************************


Proxmox Virtual Machine Builder with Cloud Images

You can have a virtual machine created and booted with the information you set within two minutes. Auto downloads the cloud image if you need it and once all the information is set it auto starts it for you.

This script can be used for beginners that don't know much about Proxmox yet or it can be used by advanced users to get a bunch of different VM's running in no time.  (Pro tip give it your ansible key when asked for keys and then run your playbook after creation)



How To Run the script
  
   1) First download the script vmbuilder.sh from github onto your proxmox node
   2) Then you need to chmod +x vmbuilder.sh
   3) If using SSH keys know the file location
   4) Make sure you have snippets enabled on one of your storage options. In the Proxmox GUI go to Datacenter then Storage to see if you have it enabled or not
   5) Then ./vmbuilder.sh
   6) Then just follow the onscreen script questions and you will be up and running in no time!



Features
 If you are in a cluster environment you are able to pick the Proxmox node to have it on (by the way of qm migrate)
 It will download the image for you if you don't have it
 It builds a user.yaml file and adds it as a snippet - so you can customize a lot of the cloud image VM when creating it (See Proxmox Wiki about snippets to learn more)
 It checks what storage is availabe on your Proxmox node and you are able to pick what you want to use
 It checks what snippet storage is availabe on your Proxmox node and you are able to pick what you want to use
 You can customize:
   - Hostname
   - ID number (It checks ID's in the entire cluster and also provides next number if you don't use custom numbers)
   - Username
   - Password
   - Add a SSH key file (example id_rsa.pub)
   - Asks if you want to enable SSH password authentication (Keys are safer)
   - Select storage you want to run the Virtual Machine on
   - Select the storage location of your ISO files
   - Select the storage and location of your snippet files (for user.yaml)
   - Check if you want to use DHCP or enter Static IP
   - If you want to enter a VLAN number
   - If you want to resize the cloud image storage so you can have more space
   - It lets you set the number of cores and memory for the Virtual Machine
   - Asks if you want it to install qemu-guest-agent (see Proxmox's wiki for more infomation) - Great to have out of the box from the Admin side of Proxmox
   - Added the option to start after creation or not to start
   - Asks what Proxmox node to have the VM running after all is complete
   - Makes it simple to learn some of the CLI of proxmox (by reviewing the script) and some awesome built in featues of Proxmox to get things up and running fast and easily
 Cloud Images currently available with this script
   - Ubuntu Focal 20.04
   - Ubuntu 20.04 Minimal
   - CentOS 7
   - CentOS 8
   - Debian 9
   - Debian 10
   - Ubuntu Bionic 18.04
   - Rancher OS
   - Fedora 32
   - More to come or request one to be added to this script

 Added 2/10/2021
   - VM's now have a default VGA set to QXL
   - VM's now have the machine set to q35
   - Took out asking for password several times
   - Took out some un-needed things that were pointed out
   - Working on removing a few more things that are really not needed

 Added 01/06/2021
   - Can now only select VLANS between 0 and 4096

 Added 01/03/2021
   - Can now select which VMBR to use

 Added 01/02/2021
   - Tablet pointer is disabled by default
   - Cleaned up some of the wording
   - Working on VMBR choices - hopefully in a day or two I will have that option avail
   
 Added 12/04/2020
   - Option to just hit enter on VMID number and accept default

 Added 11/26/2020
   - Option to enable protection on the VM
   - Option to turn it into a template
   - Added Ubuntu Groovy 20.10 Cloud Image as an option  
  
 Future things for the script
  
    - Add an option to use IPV6 or IPV4
    - Alpine Linux
    - Arch Linux
    - Rancher OS works, but auto loads in and does not use username/password but the other variables work
    - Fedora Cloud Image works, but doesn't transfer all user.yaml (like host name) snippet info yet...but works with username/password/sshkeys
    - CentOS 8 Cloud Image works, but doesn't transfer all user.yaml (like host name) snippet info yet...but works with username/password/sshkeys 
