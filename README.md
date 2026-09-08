<p align="center">

<h1>Editing File Permissions</h1>
In this project, I created a shared file and configured permissions in Active Directory to control which users could access it. I tested the permissions by signing in as different users and verifying their access.

- Microsoft Azure
- Virtual Machine 1 (Client-1)
- Virtual Machine 2 (Domain Controller/DNS Server)
- Remote Desktop
- Active Directory

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)


<h2>Deployment and Configuration Steps</h2>

To create the test environment for this demonstration, I used 2 virtual machines created here (https://github.com/JMW814/creating-azure-vms) 

I also used an Active Directory environment created here: https://github.com/JMW814/configuring-active-directory/blob/main/README.md
 
 Step 1
 
First, I need to set the group policy

I started by opening Group Policy Management and entering the security policy on my domain. I set the maximun password attemps to 5 before the account gets locked out for 10 minutes 
<p>
<img width="771" height="389" alt="group policy 1" src="https://github.com/user-attachments/assets/59c97f59-db69-4504-9e2d-af6edf32a751" />

</p>
<p>
Step 2
 
Next, I randomly chose one of the thousands of users I created and attempted to log in to their account on my client-1 virtual machine while deliberately using the incorrect password
</p>
<br />

<p>
<img width="344" height="292" alt="bad pass 2" src="https://github.com/user-attachments/assets/5744539e-7792-4ef7-ada4-e885d99515f7" />



</p>
<p>
 
Step-3
 
After 5 attempts, I was officially locked out of the account 


<p>
<img width="422" height="118" alt="account lock 3" src="https://github.com/user-attachments/assets/c6ea861d-7107-4210-9d72-a053ed318b77" />


</p>
<p>

</p>
<br />
I then went back into DC-1 and opened Active Directory

I then navigated to the experiment account and unlocked it from there

<p>
<img width="319" height="380" alt="unlock account 4" src="https://github.com/user-attachments/assets/fbd9d185-5ea0-49e1-a794-3c050ac94403" />


</p>
<p>
Step 5
Finally, I went to log in to the experiment account, and it was successful 

<p>
<img width="704" height="423" alt="login success 5" src="https://github.com/user-attachments/assets/c5af38e3-03b2-46e3-975b-891d87cffd54" />


</p>
<p>
</p>
<br />
<h2>Conclusion</h2>
This lab provided hands-on experience with Active Directory account lockout policies and user account troubleshooting. I learned how lockout policies help protect user accounts and how to unlock an account when a legitimate user becomes locked out.
