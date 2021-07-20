# Private-Network-in-Virutal-Box
A step by step process through creating a local virtual private network using Virtual Box 6.1.22 (July 2021). This virtual network will comprise an Ubuntu Desktop machine (20.04.2.0 LTS) that will eventually host a web server that will be reached by a future machine on the network.
## Description

  This will be the first project in a series of many projects that will lay the foundation on creating a stable, secure, functioning, and efficient web apache server. In this first project I will go over the process of just laying the groundwork of the whole journey: the creation of two virtual machines and connecting them through a private network. This will require a download of the current version of VirtualBox which can done here with a simple click of a button:https://www.virtualbox.org/wiki/Downloads
## Getting Started

### Prerequisites:
*   Virtual Box 6.1.22
*   An Internet Connection
*   A host computer machine
### Process:
#### Setting up the Ubuntu Server Machine
* (Process is done from top to bottom; directions are made as detailed as possible so as to lessen confusion)
* Download the Ubuntu Desktop 20.04.2.0 LTS ISO file: https://ubuntu.com/download/desktop
* Open the Virtual Box Program
* Click on the blue 'New' button on the top middle area of the window.
* Name your machine, in this case, I called it 'Ubuntu Server F' (The program might recognize the 'Version' and 'Type' based off of keywords in the name you give) and then click 'Next'.
* Set the memory size to the default 1024 MB and then click 'Next'
* Confirm that the 'Create a virtual hard disk now' option is clicked and then click 'Next'
* Confirm that the 'VDI (VirtualBox Disk Image)' option is clicked and then click 'Next'
* Confirm that the 'Dynamically allocated option’ is clicked and then click 'Next' (This sets it up so that the space that the virtual machine takes up is always at its minimum possible amount since its size changes through time)
* Set the file locations and size to whichever you see fit; I set mine to 20 GB.
* Once the machine now shows up as an option in the left hand menu, click on it so that it's highlighted in blue.
* Click the orange gear 'Settings' option on the top middle area of the window.
* A new window should pop up with the title of your new virtual machine machine.
* Click on the 'Storage' tab on the left hand side of the new window.
* Click the 'Empty' button that's under the 'Controller IDE' tab in the middle area of the window so that it's highlighted in blue.
* Click on the picture of a disk on the left portion of the screen and a small dropdown menu should appear.
* Click the 'Choose a disk file...' option and a file explorer window should show up if you are on a Windows host machine
* Go to the folder that you downloaded the ISO file in, for me it was in the 'Downloads' folder.
* Click the 'OK' button on the bottom of the window.
#### Setting up the private network
* Click on the 'Tools' tab on the left of the main Virtual Box window so that its highlighted in blue
* Click on the orange wrench 'Preferences' tab in the top middle area of the window
* A new window should pop up and be titled 'VirtualBox - Preferences'
* Click on the 'Network' tab on the left on the new window so that it's highlighted gray
* Click on the green button on the far right side on the window to add a network
* A new network titled 'NatNetwork' will automatically be created and will be displayed in the main portion of the window
* Double click the 'NatNetwork' tab and a new window will pop up with the title, 'NAT Network Details'
* Configure the network with whatever name, and CIDR you'd like. I chose the default name of 'NatNetwork' but changed the Network CIDR to 10.0.10.0/24 (In the future I will refer to my own network configurations)
* Click the 'OK' button at the bottom of the window
* Click the 'OK' button on the 'Preferences' window
* Click on the 'Ubuntu Server 1' in the main VirtualBox window
* Click the orange gear 'Settings' option on the top middle area of the window.
* A new window should pop up with the title of your new virtual machine machine.
* Click on the 'Network' tab on the left side of the new window so that it's highlighted gray
* Click on the 'Adapter 2' tab in the main portion of the window; this sets up the private network on the Ubuntu Server machine
* Click the 'Enable Network Adapter' option to enable the second adapter
* Click the 'Attached to:' drop down menu
* Click the 'NAT Network' option from the drop down menu
* The 'Name:' should automatically become the name of the private network that was named earlier
* Click the 'OK' button at the bottom of the window
* Click on the green arrow 'Start' button on top middle portion of the main Virtual Box menu
* A new window should pop up that displays the new Ubuntu Desktop running
#### Configuration of Ubuntu Machine
* After the machine loads, a screen displaying languages and options for ‘Try Ubuntu’ and ‘Install Ubuntu’ will pop up.
* Confirm your language by clicking over the language you wish
* Click on the ‘Install Ubuntu’ button.
* Select your keybodard’s layout and language.
* Click ‘Continue’
* Keep the ‘Normal Installation’ option ticked and tick the first option (Download updates while Installing Ubuntu) in the bolded ‘Other options’ section
* Click ‘Continue’
* Leave the default installation type; you are installing Ubuntu on your VirtualBox, not on your actual machine
* Click ‘Install Now’
* Click ‘Continue’
* Select a geographical region for time zones
* Click ‘Continue’
* Input credentials for your name, the computer’s name, the username, and the password.
* Click ‘Continue’
* Wait for the installation to complete
* This might take some time
* After the installation is complete, a new window should pop up prompting a restart
* Click ‘Restart Now’
* Press ‘Enter’ at the screen that says ‘Please remove the installation medium, then press ENTER:’
* The system will now restart and you will be greeted to a standard login page.
* Login with your credentials
#### Testing the local private network
* Right click on the desktop and select the ‘Open in terminal’ button
* Input the following command to download the network tools:
```
sudo apt install net-tools
```
* Input your password
* Once installed, input the following command to see your network information:
```
ifconfig
```
* If everything was done correctly, you should now see 3 different sections for IP addresses and one of them should contain the IP address belonging to the subnet that was selected earlier for the NAT Network.
## Acknowledgments
* Tutorial for Ubtunu Installation: https://www.youtube.com/watch?v=x5MhydijWmc


