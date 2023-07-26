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
<br/>
<br/>
3. You can tell the difference based on their network connectivity and the IP addresses already assigned to them. The external network is already working and DHCP has already assigned a working IP address to it. The internal NIC has no connectivity and an automatically assigned IP address because the DHCP could not provide one. I have already named both to make them easier to find.  <br/>
<img src="https://i.imgur.com/2025M7i.png" height="80%" width="80%" alt="Windows2019VirtualMachine"/>
<img src="https://i.imgur.com/wJwQELY.png" height="80%" width="80%" alt="Windows2019VirtualMachine"/>
<br/>
<br/>
4. The next step is to Assign the Internal NIC an IP Address. This is done by right-clicking the Internal network and selecting Properties. In Properties, select Internet Protocol Version 4 and insert the following:<br/>
- IP Address: 172.16.0.1 (Private IP Address Only Visible on LAN)<br/>
- Subnet Mask: 255.255.255.0<br/>
- Default Gateway: You can keep this blank<br/>
- Preferred DNS server: 127.0.0.1 (We are using this server as the DNS server, so we will use the loopback address 127.0.0.1 to call back on itself)
<img src="https://i.imgur.com/lMmgRJQ.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
5. To make things more organized and easier to remember, rename the Windows Server 2019 machine. I renamed mine "DomainController" to keep things simple. You can get here by searching "About this PC" in the system settings. <br/>
<img src="https://i.imgur.com/JRjJB8m.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
6. At this point, we have created and renamed the Windows 2019 Server virtual machine (DomainController) and configured both the External and Internal NICS. Next, we will create the Domain.  <br/>
<img src="https://i.imgur.com/U2TW4Z8.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
7. The next step is to create the Domain. Return to the Server Controller and choose Add Roles and Features. This brings you to an installation wizard. Click next until you get to Select Destination Server. Choose the server you want to use to create the Domain (Windows 2019 Server). After you choose the Windows 2019 Server, click next and choose Active Directory Domain Services. This is the last option before clicking through and finalizing the installation. <br/>
<img src="https://i.imgur.com/GZKRm7A.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/n5grEAj.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/ParRv7l.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/ZN2wXGg.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
8. After installing Active Directory Domain Services, we need to create the domain controller. Check the notification on the Server Controller that is shown as the flag in the top right corner. It will ask to promote this server to a domain controller. It will ask for you to name the domain (You can name it anything you want). Then, click next and create an easy-to-remember password for the DSRM password. After creating the password, click "next" until you are at the end and can click "install". It will restart your virtual machine. <br/>
<img src="https://i.imgur.com/p5HGHHn.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/bqXSWe1.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/N4lICCc.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
9. Once the Domain Controller boots back up, sign in and find Active Directory Users and Computers under Windows Administrative Tools. <br/>
<img src="https://i.imgur.com/B3AEpSg.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
10. Find the name you used for the Domain Controller. Mine is mydomain.com. Right-click and select "New" to create a new "Organizational Unit". This will be a new unit for your administrator account. Fill out the user credentials and create a password for the account. <br/>
<img src="https://i.imgur.com/Xx9DYC0.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>  
<img src="https://i.imgur.com/7AzlP6v.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/aSeydx4.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/Aj9G5UZ.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>  
<img src="https://i.imgur.com/fGAmw5g.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
11. Under the user we just created, go to Properties and add the user to a new group. You can find groups under the MemberOf tab. I named the group Domain Admins because this will be the group assigned to administrators in this domain. After setting up the group, click apply and sign out of the machine. You can now log into your new user account.<br/>
<img src="https://i.imgur.com/fLmao0e.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/ekowY6T.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
12. Next, we are going to install RAS and NAT on the Domain Controller to allow the Windows 10 Client virtual machine to access the internet through the Domain Controller. This is similar to the Active Directory Domain Services step. However, we are going to install RAS additionally. Again, go to the Server Controller and choose Add Roles and Features. Click through until you can select server roles and check Remote Access. Once checked, click next until you can check Routing. DirectAccess and VPN (RAS) will automatically be checked. After checking Routing and RAS, click until you can begin the installation. <br/>
<img src="https://i.imgur.com/oCjjVjc.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/eHqxwig.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/5u5riAR.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
13. The next step is to configure NAT on our Domain Controller. Go to Tools in the top right of the Server Controller. Scroll down to Routing and Remote Access. This will bring you to a window where you can configure the server. Right-click the domain controller we have created (Mine is Domain Controller) and choose Configure and Enable Routing and Remote Access. Click next and choose the Network Address Translation (NAT) option. Now, choose the external NIC we named earlier. This will be used to route the Windows 10 Client to the internet through the Domain Controller. Click next and hit install. <br/>
<img src="https://i.imgur.com/EgRkeYU.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/Kb2Tqjo.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/sY5BaKi.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/QW2GlFn.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
14. Step 14 is creating a DHCP server in the Domain Controller to assign an IP address to the Windows 10 Client and other clients if you build onto this project. First, start at the Server Controller and go to Add Roles and Features. Click "next" until you find your server roles and install DHCP. After checking DHCP, click next until you install the service. <br/>
<img src="https://i.imgur.com/vhFuuFz.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/c2NpnD6.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
15. Step 15 is creating the scope for the DHCP server. Scroll over to Tools in the Server Controller and click DHCP. It will bring you to the DHCP configurations. Scroll over IPV4 and select New Scope. In this tutorial, I will be naming the scope DHCPScope1. Click next once you name the scope. This brings you to an installation wizard where you can enter the IP range we are going to use for this DHCP server. We will be using 172.16.0.100-172.16.0.200. Once you have entered the IP range, click next after the Exclusions and Delay screen. We can keep the IP Lease Time at default. 8 days is enough for our case. Continue and Click "Yes" to configure DHCP options. The first configuration is the Router Default Gateway. Configure this to be 172.16.0.1. Make sure to hit Add. The next configuration is the DNS server. We already configured that in a previous step, so we can click next. We aren't using WINS Server, so we can click next. Next, click "Yes" and activate the scope. Finally, scroll back to the DHCP configurations and authorize the DHCP server. IPV4 will also need to be refreshed to show as active. <br/>
<img src="https://i.imgur.com/pc3vGKI.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/HIPCldU.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/qauvnun.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/PEfyJM1.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/qFv3tz9.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/xvCn80s.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
16. The next step is to enable browsing on the server. You shouldn't do this in a live environment, but we are going to download a PowerShell script to bulk create users. Go to the Server Controller and on the left side, you can choose Local Server. In the properties, choose IE Enhanced Security Configuration and turn it off. This allows you to browse using Internet Explorer. Now, we can download our scripts from the ActiveDirectory repository files [link](https://github.com/JaedonMallory/ActiveDirectory). I added notes to the script to give a brief generalization of what the code does. <br/>
<img src="https://i.imgur.com/e8vNCBy.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
17. Once the PowerShell script is downloaded, we can begin creating the users. Go to the taskbar and run PowerShell ISE as an administrator. This is needed to make sure all permissions are met to create the users. <br/>
<img src="https://i.imgur.com/E5n4MP1.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
18. With PowerShell running, we can open the script by clicking the folder icon called Open Script. In the case of this tutorial, we are going to use Password1 for all user passwords to make the demonstration simple. We could generate 1,000 unique passwords for each user and extract them from a database to simulate real users with real passwords. However, this works as a beginning setup. The script requires Set-ExecutionPolicy to be unrestricted. Additionally, we must change directories to locate the script and run it. Do this by typing C:\Users\(your account username)\(location)\(name of the script). Mine looks like C:\Users\a-jmallory\Downloads\PowerShell Script AD. You can look inside the directory and list out the contents by using the "ls" command to make sure you run the correct script. Finally, run the script. You can either hit the green Run button in the terminal or type out the script name in the command line. Mine looks like .\1_CREATE_USERS.ps1. When it asks to make sure you want to run the script, click Run. Your users will take some time to create, but once you run the script, it will automatically create all of them, and you can check in the Active Directory Users and Computers configuration menu. <br/>
<img src="https://i.imgur.com/E5n4MP1.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/EKVqTD1.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/sroWhzN.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/N9kNc3j.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/wsOUXlF.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/r9v55rg.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/kCL4CSv.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
19. With the Domain Controller and basically everything set up, we can move on to the Windows 10 Pro Client. If you need help setting up a  Windows 10 Virtual Machine, refer to this [tutorial](https://github.com/JaedonMallory/Windows10VM) (Just choose Pro instead of Home). We also need to change the network settings in VirtualBox on the Client. The change will be from NAT to Internal, as we want the Client to route through the Domain Controller and not the Internet. Next, we can see as we open up the Command Prompt and check the network configuration that the DHCP server and DNS server are working properly. The DHCP is providing the Windows 10 Pro Client with an IP Address, and it is in the range we configured. <br/>
<img src="https://i.imgur.com/ZngWEYq.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/nNCxwQB.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
20. With everything running as it should be, we can finally join the Domain with our Client. This is going to be similar to when we renamed our Domain Controller. First, go into the System Settings and Find About, or type About this PC into the taskbar. Scroll further down than Rename this PC until you get to Rename this PC (advanced). Once you are in System Properties, click Change to rename the computer. Rename the Client to whatever you want (Mine is Client) and type the name of the Domain Controller into the Domain section. (Mine is mydomain.com). Click Ok and a window asking for you to sign in will pop up. Use the original Administrator username and password we created at the beginning. You will then need to restart your Client. <br/>
<img src="https://i.imgur.com/qqOeP5Y.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/sCxtsc4.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
20. Finally, we have our Domain Controller and Client setup. We can see our Client shown in the Active Directory Users and Computers configuration. This allows us to log in as a separate user we created during the PowerShell sequence, or we can log in as our admin account. I ran the whoami and ping commands to show everything is connected and the domain is available to be used.<br/>
<img src="https://i.imgur.com/eGHVbsm.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<img src="https://i.imgur.com/kwkThE4.png" height="80%" width="80%" alt="Windows10VirtualMachine"/>
<br/>
<br/>
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
