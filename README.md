# ActiveDirectory
<h1>Active Directory With 1000+ Users Tutorial</h1>

<h2>Description</h2>
This project consists of a simple tutorial for setting up a basic Active Directory Home Lab. It walks the user through each step of setting up a Windows 2019 Server virtual machine on their desktop through VirtualBox 7. Virtual machines are extremely useful and can be set up very quickly. In this tutorial, I use multiple virtual machines to simulate an Active Directory environment that you would see in a work environment with 1000+ users. The first virtual machine, the Windows 2019 Server, will be acting as the domain controller for the environment. We will need to connect the Domain Controller to the internet and to the internal network along with the Windows 10 machine. DHCP will automatically configure the IP address on the external-facing NIC, but we will need to give the internal-facing NIC the correct network configurations.
<br><br/>

Click this [link](https://github.com/JaedonMallory/Windows10VM) to watch the Windows 10 Virtual Machine walkthrough if you need help setting up a virtual machine


<h2>Utilities Used</h2>

- <b>VirtualBox 7(https://www.virtualbox.org/wiki/Downloads)</b> 
- <b>Windows 10 ISO (https://www.microsoft.com/en-us/software-download/windows10ISO)</b>
- <b>Windows 2019 Server ISO (https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019)</b>

<h2>Environments Used </h2>

- <b>Windows 10</b>
- <b>Windows 2019 Server Desktop Environment</b>

<h2>Program walk-through:</h2>

<p align="center">
1. Once you have downloaded the Windows 10 ISO file and VirtualBox, Click New in VirtualBox. This prompt will ask for you to name your new Virtual Machine and ask for the ISO file you want to use.: <br/>
<img src="https://i.imgur.com/IhLub4X.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br />
<br />
2. Select the Windows 10 Version you want. In this case, we are going to use Windows 10 Home:  <br/>
<img src="https://i.imgur.com/puARyM4.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br />
<br />
3. Click the checkbox to install Guest Additions for better performance. Make sure all other checks are green to proceed. <br/>
<img src="https://i.imgur.com/euwqOKp.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
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
