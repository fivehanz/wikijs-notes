<!-- TITLE: VM MCC -->
<!-- SUBTITLE: How to install MCC app on VM -->

# Step 1: Install VMWare Player
https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/15_0

* I have installed VMWare Workstation Player 15.0 on a Ubuntu based linux.
* VMware Player is free for non-comercial usage.
* Download and Install VMWare Player

# Step 2: Download Windows XP ISO
* Download any genuine Windows XP SP3 ISO from Microsoft website.


# Step 3: Create VM using VMware Player
## Select "**Create a New Virtual Machine**" on VMware Player.
![Vmplayerisoselect](/uploads/vmplayerisoselect.png "Vmplayerisoselect")

## **Select a Name for your VM**
![Vmxpwizname](/uploads/vmxpwizname.png "Vmxpwizname")
 
## **Select NEXT and YES when asked for key. (You can search for a key online available for free to enter at this stage or after installation.)**
![Vmpxpkeyaskvm](/uploads/vmpxpkeyaskvm.png "Vmpxpkeyaskvm")
* 
* PS: It asks later for key while setup. (I have used, ***QHYXK-JCJRX-XXY8Y-2KX2X-CCXGD***)

## **Select your desired disk size** 
![Vmxpwizdisksize](/uploads/vmxpwizdisksize.png "Vmxpwizdisksize")

## **Finish Installation, check automatically start the VM**
![Vmxpwizfinish](/uploads/vmxpwizfinish.png "Vmxpwizfinish")
 
## Auto-start of VM will continue with the setup.
![Vmplxpsetup](/uploads/vmplxpsetup.png "Vmplxpsetup")
 
 
# Step 3: Copy MCC files inside VM
* **Connect flash drive and copy MCC setup files into C: Drive of virtual machine.**
* **Rename it to "DISK1"**

### MCC to DISK1
![Wxpredisk 1](/uploads/wxpredisk-1.png "Wxpredisk 1")

# Step 4: Run the installer (setup)
* Navigate to inside the folder
* Select the Setup
* Click **Continue** -> **New Installation**

### Let the default folder be WINMAC
![Wxpmccinswinmac](/uploads/wxpmccinswinmac.png "Wxpmccinswinmac")

### Shared Marking Data Folder

* Leave it **blank by default**. **if error persists, create a new folder by anyname in C: Drive and type the path of this new folder here.**


# Installation
* run the setup file from DISK1
* Error 1: Shared folder, leave it blank.
* If that doesn't work, create a folder and put the path of the folder.
* 
* ![Sharedmcc](/uploads/sharedmcc.png "Sharedmcc")

**That are the main steps to install MCC**
