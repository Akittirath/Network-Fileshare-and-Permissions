<p align="center">
<img src="https://i.imgur.com/AeiqMDZ.png" alt="Traffic Examination"/>
</p>

<h1>Network-File-Shares-and-Permissions</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Domain Controller/Client Machine)
- Remote Desktop
- Shared Network Files

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

</p>
<p>
In this lab we will be setting up shared network files & permissions. We will create folders in the DC-1 VM and share them on the network certain files will have certain permissions. Only people we allow will have access to these permissions. First we will open up file explorer, click this PC, go to the c:/ drive on the DC-1 machine and create 4 folders. "read-access" "read/write-access" "no-access" and "accounting".
</p>
<br />

<p>
<img src="https://i.imgur.com/rVmNvn6.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After the folders have been created what you want to do is share them on the network so that the client-1 machine can view them. We can also set the permissions of the folders in DC-1. Set the folders to the appropriate permissions. Domain users should have permissions to "read-access-, Domain users should also have permissions to "write-access". Lastly "no-access" should have read/write permissions for domain admins only. Giving domain admins this much permissions means they are higher up then domain users. We will leave accounting folder alone for now.
</p>
<br />

<p>
<img src="https://i.imgur.com/hrK39QL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next step is, we will head back over to client-1. In order to see the files we have created in Client-1 VM, we will type in "\\dc-1 in file explorer. It should eventually pop up.
</p>
<br />

<p>
If we login to the client machine with a normal user account we can test out the shared files we just created. As you can see the permissions that we set are working properly. No-access only domain admins can enter. In the write-access, the domain users can access and write a text or file inside. That means that is great news!
</p>
<br />
<p>
<img src="https://i.imgur.com/dsV1po3.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/tpKVBTh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
Go back to the DC-1 VM. In AD create a security group called "Accountants" the users assigned to this security group will be the only ones allowed to view the "Accountants" folder. We have to share the "Accountants" folder just like we did in the last section, this we will be sharing it to only the accountants group. Normal users will not have access to this folder. If we wanted to give a normal user access to the accounting folder they would have to be a part of the "Accountants" security group.
</p>
<br />
<p>
<img src="https://i.imgur.com/7XnRTmk.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.https://i.imgur.com/qQoN1Di.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/dlKEco0.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p>
<img src="https://i.imgur.com/OeSE08W.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
In order for an "Accountant" to access this folder, we will need to add a domain user. We will add the domain user we are logged into, and add him/her to the member of the accountant team. After you have added the domain user, we will need to restart your Client-1 VM and logged back into the domain user. It will then let you access the folder Accounting. That is it! You have completed the networking fileshare and permissions lab. 
