<p align="center">

<h1>Editing File Permissions</h1>
In this project, I created a shared file and configured permissions in Active Directory with folder properties and security groups to control which users could access it. I tested the permissions by signing in as different users and verifying their access. The goal is to see how changing permissions affects the other users in the domain

>
Technologies and Environments Used 

- Microsoft Azure
- Virtual Machine 1 (Client-1)
- Virtual Machine 2 (Domain Controller/DNS Server)
- Remote Desktop
- Active Directory
- File Explorer

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)


<h2>Deployment and Configuration Steps</h2>

To create the test environment for this demonstration, I referenced 2 virtual machines created here (https://github.com/JMW814/creating-azure-vms) 

I also used/referenced many elements from an Active Directory environment created here: https://github.com/JMW814/configuring-active-directory/blob/main/README.md
 
 
To start, I used Remote Desktop to log into DC-1, opened File Explorer, went into the C: drive, and created 3 folders: Read access, Write access, and No access 
<p>
<img width="1182" height="786" alt="image" src="https://github.com/user-attachments/assets/b4e88674-5f4d-4a97-befd-ae92eaa7a6c7" />

</p>
<p>
 
I then shared each folder and gave different permissions to each of them:

Read access = Domain users can read the folder 

Write access = Domain users can read and write in the folder 

No access = only Domain admins can read or write in it  

</p>
<br />

<p>
<img width="1181" height="871" alt="image" src="https://github.com/user-attachments/assets/83f60135-31e6-4015-8c13-fbe9cc609bc7" />



</p>
<p>
 
 
Once those were created, I logged into client-1 with one of the normal users (loqe.six) I created in Active Directory. I went into DC-1’s C: drive to see its shared folders and  to test its access to these folders

Read access = loqe.six can only open the folder 

Write access = loqe.six can open the folder and create documents in it 

No access = loqe.six can’t even open the folder   


<p>
<img width="1447" height="336" alt="image" src="https://github.com/user-attachments/assets/8e9c0d2e-0e1a-4606-9d44-3330ba155743" />


</p>
<p>

</p>
<br />
After this, I wanted to test permissions with security groups. To do this, I first switched back over to dc-1 and went into Active Directory


In Active Directory, I first created an Organizational Unit named “groups” and a security group within it named “accounting”

<p></p>
<p>
<img width="872" height="510" alt="image" src="https://github.com/user-attachments/assets/ce802463-7e80-41be-8f6b-a6a35231dbb6" />


</p>
<p>

I then opened File Explorer, went into the C drive, and created another folder to share named “accounting,” and set the permissions to only allow read and write  access to members of the “accounting” security group 
<p>
<img width="1304" height="706" alt="image" src="https://github.com/user-attachments/assets/0cf4a0d4-80f6-403f-9c56-11945b2a0cf6" />



</p>
<p>

 I went back into the loqe.six account on client-1 and tried to access the file, but was ultimately denied access to it.
<p>
<img width="1407" height="627" alt="image" src="https://github.com/user-attachments/assets/c7440e25-7486-48be-8e32-8b84b056ab2a" />

 </p>
<p>
Step 6

I want loqe.six to have access to the accounting folder

To troubleshoot this, I went back into DC-1’s Active Directory and moved loqe.six into the accounting security group 
<p>
<img width="1024" height="552" alt="image" src="https://github.com/user-attachments/assets/85236283-9272-435e-9a40-b8cd28eed54a" />

 
 </p>
<p>

I went back into client-1 and now loqe.six has full read and write access to the accounting folder
 
<p>
<img width="1302" height="524" alt="image" src="https://github.com/user-attachments/assets/1f75cff8-5f9f-40b9-925c-872277136915" />
</p>
<p>
</p>
<br />
<h2>Conclusion</h2>
This lab provided hands-on experience with file sharing and user permissions in an Active Directory environment. I learned how to grant and restrict access to shared files based on user permissions. I also observed how file sharing interacts with security groups.
