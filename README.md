# ActiveDirectory
<h1>Active Directory Home Lab With 1000+ Users</h1>

<h2>Description</h2>
<img src="https://i.imgur.com/yz4fGby.png" height="80%" width="80%" alt="Figure1"/>
This project consists of a simple tutorial for setting up a basic Active Directory Home Lab. It walks the user through each step of setting up a Windows 2019 Server virtual machine on their desktop through VirtualBox 7. Virtual machines are extremely useful and can be set up very quickly. In this tutorial, I use multiple virtual machines to simulate an Active Directory environment that you would see in a work environment with 1000+ users. The first virtual machine, the Windows 2019 Server, will be acting as the domain controller for the environment. We will need to connect the Domain Controller to the internet and to the internal network along with the Windows 10 machine. DHCP will automatically configure the IP address on the external-facing NIC, but we will need to give the internal-facing NIC the correct network configurations. Once all of the network configurations have been established, we will add 1000 users via PowerShell.
<br><br/>

Click this [link](https://github.com/JaedonMallory/Windows10VM) to watch the Windows 10 Virtual Machine walkthrough if you need help setting up a virtual machine


<h2>Utilities Used</h2>

- <b>VirtualBox 7(https://www.virtualbox.org/wiki/Downloads)</b> 
- <b>Windows 10 ISO (https://www.microsoft.com/en-us/software-download/windows10ISO)</b>
- <b>Windows 2019 Server ISO (https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019)</b>

<h2>Environments Used </h2>

- <b>Windows 10</b>
- <b>Windows 2019 Server Desktop Environment</b>

<h2>Known Issues:</h2>

Error: If you find a problem installing the Windows 2019 Server ISO while creating the virtual machine, opt to choose the ISO until after you create the instance. <br/>
<img src="https://i.imgur.com/Uq4H5c5.png" height="80%" width="80%" alt="Figure1"/>

Instead of choosing the ISO file at the beginning or in Figure 1, choose the ISO file once the virtual machine is made shown in Figure 2. <br/>
<img src="https://i.imgur.com/DJzBDOZ.png" height="80%" width="80%" alt="Figure1"/>
<img src="https://i.imgur.com/Zp7nPXv.png" height="80%" width="80%" alt="Figure2"/>

<h2>Program walk-through:</h2>

<p align="left">
1. After installing VirtualBox and downloading the Windows 2019 Server ISO, you want to set up the Windows 2019 Server Virtual Machine. It will be acting as our Domain Controller. The whole process is relatively the same as any other virtual machine setup, so I linked my previous Windows 10 Virtual Machine tutorial above. Create the Administrator Password after installing. You can keep it simple to remember it. <br/>
 
<img src="https://i.imgur.com/vRoTIkd.png" height="80%" width="80%" alt="Windows2019ServerVirtualMachine"/>
<br/>
<br/>
2. The next process is finding and configuring your internal and external networks. This is an easy process. Type Network Status into the Search bar in the bottom left on the taskbar. Scroll down until you see Change Adapter Options. This will bring you to your two networks.  <br/>
<img src="https://i.imgur.com/yPGOBVz.png" height="80%" width="80%" alt="Windows2019VirtualMachine"/>
<img src="https://i.imgur.com/DDMsb0y.png" height="80%" width="80%" alt="Windows2019VirtualMachine"/>
<img src="https://i.imgur.com/MPyoc1s.png" height="80%" width="80%" alt="Windows2019VirtualMachine"/>
<br />
<br />
3. I have already named mine both to make it easier to find them. However, you can tell the difference based on their network connectivity and the IP addresses already assigned to them. The external network is already working and DHCP has already assigned a working IP address to it. The internal NIC has no connectivity and an automatically assigned IP address because the DHCP could not provide one. <br/>
<img src="https://i.imgur.com/2025M7i.png" height="80%" width="80%" alt="Windows2019VirtualMachine"/>
<img src="https://i.imgur.com/wJwQELY.png" height="80%" width="80%" alt="Windows2019VirtualMachine"/>
<br />
<br />
4. Choose how much RAM you will allocate to the virtual machine. Microsoft states that a 64x version of Windows 10 needs a minimum of 2 GB or 2048 MB. <br/>
<img src="https://i.imgur.com/4oCQQBe.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br />
<br />
5. This step is similar to the previous step. Choose the amount of storage your virtual machine will have access to. Microsoft states that a 64x version of Windows 10 needs a minimum of 20 GB of storage.  <br/>
<img src="https://i.imgur.com/7W5aHCU.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br />
<br />
6. Make sure everything is shown as you want it to be. This is the last step before creating the virtual machine.  <br/>
<img src="https://i.imgur.com/OUoAQng.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br />
<br />
7. It will take a few minutes to finish installing Windows 10. Once it is done, click through the installer while following the instructions. <br/>
<img src="https://i.imgur.com/YNsVupa.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br />
8. That's it! You just installed your first, and hopefully not last, Virtual Machine on VirtualBox! <br/>
<img src="https://i.imgur.com/z0rMMCl.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
