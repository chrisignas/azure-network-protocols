<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Resources
- Observe IMCP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/ejUuv6y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a Resource Group
</p>
<br />

<p>
<img src="https://i.imgur.com/RL3keev.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create the first virtual machine as Windows 10 within the Resource Group
</p>
<br />

<p>
<img src="https://i.imgur.com/ioiT6F8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Leave the Subnet and IP Address as default.
</p>
<br />

<p>
<img src="https://i.imgur.com/FDiPf8K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create the 2nd VM as a Ubuntu machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/bw2nw8L.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Setup an Admin Account with a Password. Remember this or write it down.
</p>
<br />

<p>
<img src="https://i.imgur.com/qCalW6t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Make sure the virtual network is the vnet (RG-Lab-02-vnet) which was automatically created. Then finish by clicking create at the bottom.
</p>
<br />

<p>
<img src="https://i.imgur.com/4V5xfsJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Both VM's and resources should now have been created.
</p>
<br />

<p>
<img src="https://i.imgur.com/1IOPbZt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open the Network Watcher resource. You can search for it in the search bar at the top. Click Topology on the left hand side. 
The topology of the network will be visible with both VM's within the resource group.
</p>
<br />

<p>
<img src="https://i.imgur.com/AaqDWwx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Connect to the Windows VM using its Public IP Address. Click on VM1 and you'll see the public IP address under Networking.
</p>
<br />

<p>
<img src="https://i.imgur.com/0W68dge.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this example, the connection was made with Microsoft Remote Desktop for Mac. Remote Desktop can be used for PC's.
</p>
<br />

<p>
<img src="https://i.imgur.com/NcsG3BD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Edge browser within the VM and download Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/W75GrCx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/y0itrl7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, launch Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/eRFlWWf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click the green fin icon on top left corner to start capturing packets.
</p>
<br />

<p>
<img src="https://i.imgur.com/IIYeDl7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Let's filter traffic by ICMP
</p>
<br />

<p>
<img src="https://i.imgur.com/6fmevOE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to VM2 and copy the private IP address just as you did with VM1 and its public IP address. The private will be below the public one.
</p>
<br />

<p>
<img src="https://i.imgur.com/kG8OS4r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open PowerShell in VM1. Search for it in the search bar on the bottom left.
</p>
<br />

<p>
<img src="https://i.imgur.com/csn7wmQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ping the private IP by typing "ping" and the private IP address as shown above. You can see the requests and replies to VM2 and back to VM1 on Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/iVsnfd8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now try pinging Google and forcing an IP v4 address with "ping www.google.com -4". Observe the traffic being sent to and received from Google.
</p>
<br />

<p>
<img src="https://i.imgur.com/L4OchQ1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on a line of traffic and see the data being sent. Check out the random alphabetical data mid right that's being sent.
</p>
<br />

<p>
<img src="https://i.imgur.com/RTNH00Q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on the green fin on the top left to clear the traffic data.
</p>
<br />

<p>
<img src="https://i.imgur.com/YEBOMnR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now do a continuous ping with the private IP and "-t" command. Example: 10.0.0.5 -t
</p>
<br />

<p>
<img src="https://i.imgur.com/wVH336O.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Notice the nonstop pinging. We will now block it with a firewall.
</p>
<br />

<p>
<img src="https://i.imgur.com/FdVkvZO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Network security groups in Azure.
</p>
<br />

<p>
<img src="https://i.imgur.com/qBEjTJJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open VM 2 Network security group.
</p>
<br />

<p>
<img src="https://i.imgur.com/1BEnv8S.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open inbound security rules on the left.
</p>
<br />

<p>
<img src="https://i.imgur.com/CvOVc7N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click Add on the top to add a new rule to deny ICMP from anywhere, make its priority 200 to be the first rule in line.
</p>
<br />

<p>
<img src="https://i.imgur.com/JrfMQSg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ping requests begin to timeout so the firewall is working.
</p>
<br />

<p>
<img src="https://i.imgur.com/sN4O0Y0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Edit the rule and allow ICMP traffic again.
</p>
<br />

<p>
<img src="https://i.imgur.com/Jylh3tg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Clear Wireshark and SSH into VM2 from VM1. Get VM2 private IP address from VM2 on Azure. 
</p>
<br />

<p>
<img src="https://i.imgur.com/SHAE41V.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Type 'yes' and type the password you created. Password won't show on PowerShell so don't worry. Just type it out and press enter.
</p>
<br />

<p>
<img src="https://i.imgur.com/ORgEnRA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Notice anytime you type, Wireshark shows SSH Traffic spam.
</p>
<br />

<p>
<img src="https://i.imgur.com/vhOJQ59.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Type 'exit' to close the SSH connection and go back to the VM1 command line.
</p>
<br />

<p>
<img src="https://i.imgur.com/6v7rUSd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
You can also filter SSH traffic with tcp.port == 22 on Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/lEnpffl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Filter Wireshark by DHCP. Then renew DHCP on PowerShell with "ipconfig /renew". IP address should re-issue.
</p>
<br />

<p>
<img src="https://i.imgur.com/d8SAYvW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Filter by DNS traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/kbwuFvP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Type in "nslookup www.google.com" and observe the traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/0880skB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
DNS uses port 53 so you can also filter by udp.port == 53.
</p>
<br />

<p>
<img src="https://i.imgur.com/cdwI8kt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
tcp.port == 3389 (RDP or remote desktop protocol) shows our current connection from the computer to VM1. Observe the traffic. Congratulations! That concludes the project!
</p>
<br />
