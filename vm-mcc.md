<!-- TITLE: VM MCC -->
<!-- SUBTITLE: How to install MCC app on VM -->

# Windows XP on VM
## Step 1: Install VMWare Player
https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/15_0

* I have installed VMWare Workstation Player 15.0 on a Ubuntu based linux.
* VMware Player is free for non-comercial usage.
* Download and Install VMWare Player

## Step 2: Download Windows XP ISO
* Download any genuine Windows XP SP3 ISO from Microsoft website.


## Step 3: Create VM using VMware Player
### Select "**Create a New Virtual Machine**" on VMware Player.
* ![Vmplayerisoselect](/uploads/vmplayerisoselect.png "Vmplayerisoselect")

### **Select a Name for your VM**
* ![Vmxpwizname](/uploads/vmxpwizname.png "Vmxpwizname")
* 
* **Select NEXT and YES when asked for key. (You can search for a key online available for free to enter at this stage or after installation.)**
* ![Vmpxpkeyaskvm](/uploads/vmpxpkeyaskvm.png "Vmpxpkeyaskvm")
* PS: It asks later for key while setup. (I have used, ***QHYXK-JCJRX-XXY8Y-2KX2X-CCXGD***)
* 
* **Select your desired disk size** 
* ![Vmxpwizdisksize](/uploads/vmxpwizdisksize.png "Vmxpwizdisksize")

* **Finish Installation, check automatically start the VM**
* ![Vmxpwizfinish](/uploads/vmxpwizfinish.png "Vmxpwizfinish")
* 
* Auto-start of VM will continue with the setup.
* ![Vmplxpsetup](/uploads/vmplxpsetup.png "Vmplxpsetup")
* 
* 
## Step 3: Copy MCC files inside VM


Step 1: to get MCC setup files into C: Drive of virtual machine.
Step 2: copy all files to a folder "DISK1"
Step 3: Run the installer.
# Installation
* run the setup file from DISK1
* Error 1: Shared folder, leave it blank.
* If that doesn't work, create a folder and put the path of the folder.
* 
* ![Sharedmcc](/uploads/sharedmcc.png "Sharedmcc")

**That are the main steps to install MCC**
