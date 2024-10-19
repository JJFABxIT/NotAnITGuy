# Getting started with Proxmox!
---

**Requirements**:

1. USB (over 8gb)
2. Device to install PVE too
3. Rufus (or similar)

---

## First things first

Head over to the [Proxmox Downloads](https://www.proxmox.com/en/downloads) website and download the latest ISO file. Keep note of where you saved the downloaded file, we'll need that shortly. 
Once downloaded, fire up Rufus (or whatever you use to create a bootable drive), you can find Rufus [here](https://rufus.ie/en/) create the bootable USB with the Proxmox ve iso file we downloaded in the last step. Depending on your hardware, this could take some time. Perfect time for a cuppa. 

Once **Rufus** has finished its thing, safely eject the USB and plug it into the machine you want to install Proxmox on. Boot the machine and navigate through the GUI, here you will need to **accept the license agreement**, set your time zone as well as a few other options. Configure the network settings, unless you're using DHCP, and set up the initial root user by setting the email address and creating a strong password. I cannot emphasize enough that this password needs to be strong as it will be the user with full system priviledges. 

Nearly there now, once you have gone through all the options, including setting up the storage, the installer will now go ahead and install Proxmox. The machine will reboot and ask us to **remove the USB drive**. If you didnt have a chance for that cuppa before, you will now. Once the machine reboots, you will be greeted with a terminal login screen, here we can see the IP address of the web GUI as well as the option to enter our password. Now we will switch over to another computer, fire up a browser and head over to the  address given to us on the login screen of the Proxmox host, it will be the IP address of your machine followed by ":8006". If you are unsure what the ip address is of the Proxmox host, simply log in to the physical machine and tyoe ``` ifconfig ``` or ``` ip a ```.

If you got this far, well done! You're on your way to discovering a world of possibilties with virtualisation and containerisation. I remember the excitement i felt the first time i PVE installed and working!
Log in to the web GUI using ``` root ``` as the username and the password you used during the installation. If the 3rd box asking for a **Realm** is empty, you will need to select **Linux PAM Standard**. 

### The exciting part!

Now lets create our first virtual machine. In this demo i will be using a Linux server, more specifically Ubuntu Server 22, however you can use what OS you like however the steps will vary to mine depending on the route you choose. Your mileage may vary. 

1. Create the Virtual Machine. 

- In the Promox interface, click on "Create VM". The button can be found in the upper right hand side of your screen. 

- Give it a name - Lets call it "MyFirstVM" and set the VM ID. Here you are also given some more advanced options like start at boot and specific boot order, however they are out of the scope of this demonstration as are a variety of options further throughout. 

- Click next and select the ISO image you would like to use to install on the VM. If you have not yet installed a ISO file (as many of you may not have yet), then under the hosts name under the server view on the left. Click on the system storage, most likely "local", click on ISO images and here you will find the option to Upload your desired ISO images. 

- Next we will leave the "system" settings as the defaults, click next and configure the disk settings for the VM. Leave the option on SCSI, select the Storage pool and give the VM a suitable amount of storage. The default of 32gb is more than enough. 

- Now we will configure our CPU and Memory for the VM. I have gone for 2 cores and 4gb of memory. You can set the values to what ever you like as long as the host has the suitable number of cores and memory available itself. 

- Leave the Network settings at the default values to use the host networking as a bridge to get started however you can set up a variety of options under the networking tab. I will go through some of these options in a later tutorial as we delve deeper into Proxmox. Click next and confirm the settings you have chose for the VM, click the option to "Start after created" if you are happy to and click finish. 

Click on "Console" under the VM you just created on the left to get started. Thats it! You've just created your first Virtual machine on your very own virtualisation host using Proxmox. You are well on your way to managing your own home lab, this is only just the beginning! 

