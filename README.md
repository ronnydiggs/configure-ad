<p align="center">
<img src="https://github.com/ronnydiggs/configure-ad/assets/64152064/395c8cda-7161-46f6-895e-2a5c7a8246c4" width="250"/>
</p>

<h1>Active Directory - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of Active Directory.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Client VM
- Active Directory VM

<h2>Operating Systems Used </h2>

- Windows 10</b> 
- Windows Server 2022</b> 

<h2>List of Prerequisites</h2>

- Item 1
- Item 2
- Item 3
- Item 4
- Item 5

<h2>Installation Steps</h2>

<p>
<img src="https://github.com/ronnydiggs/configure-ad/assets/64152064/d43d6f73-1b9d-4b84-9dc8-14ee5caa44b5" width="500"/>
</p>
<p>
Name the resource group AD-Lab and select the image as Windows Server 2022. Create the Virtual Machine for the Domain Controller. 
</p>
<br />

<p>
<img src="https://github.com/ronnydiggs/configure-ad/assets/64152064/56d83058-1c1d-4776-9aa5-bce8f669680f" width="500"/>
</p>
<p>
Use the same resource group AD-Lab and select the image as Windows 10 Pro. 
</p>
<br />

<p>
<img src="https://github.com/ronnydiggs/configure-ad/assets/64152064/647f8e94-ede6-4869-bdeb-542fd60e549f" width="500"/>
</p>
<p>
Go to the networking tab and change the virtual network to DC-1 vnet, so that Client 1 and Domain Controller are on the same virtual network. 
Create the Virtual Machine for Client 1.
</p>
<br />

<p>
<img src="https://github.com/ronnydiggs/configure-ad/assets/64152064/62583ba5-ad7f-4355-b49e-880420af9d32" width="500"/>
</p>
<p>
Go to the networking tab and change the virtual network to DomainController vnet, so that Client 1 and Domain Controller are on the same virtual network. 
Create the Virtual Machine for Client 1.
</p>
<br />

<p>
<img src="https://github.com/ronnydiggs/configure-ad/assets/64152064/62583ba5-ad7f-4355-b49e-880420af9d32" width="500"/>
</p>
<p>
Go to network settings of DomainController VM. Click the network interface domaincontroller180_z1. 
Go to ipconfig1 and change the private IP address to static. This is important because we want to keep the IP address from changing.
</p>
<br />

<p>
<img src="https://github.com/ronnydiggs/configure-ad/assets/64152064/9a868978-978a-4853-9da1-f35f5305bcb1 width="500"/>
</p>
<p>
Go to network settings of DomainController VM. Click the network interface client1464_z1. 
Go to DNS Servers and add the private IP address: 10.0.0.5. This is important because essentially we are making the Domain controller the DNS server for Client 1.
</p>
<br />

<p>
<img src="https://github.com/ronnydiggs/configure-ad/assets/64152064/18a7a67a-aa28-47d6-b5bb-636989bdc664" width="500"/>
</p>
<p>
As currently constructed, the two VMs cannot ping one another. We want Client 1 to be able to ping the domain controller. To do this we need to change a firewall rule to allow ICMPv4 traffic in the DomainController VM.
</p>
<br />

<p>
<img src="https://github.com/ronnydiggs/configure-ad/assets/64152064/af0ca4f9-5970-4b0a-a658-505413d2ddaa" width="500"/>
</p>
<p>
Enable firewall rule to allow ICMPv4 traffic (echo request and reply) for IP address 10.0.0.4, the Client 1 IP.
</p>
<br />

<p>
<img src="https://github.com/ronnydiggs/configure-ad/assets/64152064/3bec9090-441d-4a26-93b7-3963a1583465" width="500"/>
</p>
<p>
Test the connection between Client 1 and Domain Controller. Now the two VMs can communicate.
</p>
<br />

