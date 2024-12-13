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

  1) Handling Account Lockouts
Access the DC-1 Server

<p>
<img src="https://imgur.com/Dxs8Ad9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

2) Select a previously created user account. Attempt to log in 10 times using an incorrect password.

<p>
<img src="https://imgur.com/EKeeExY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

3) Open the Group Policy Management Console (GPMC)

Log in to a machine with the GPMC installed (usually a Domain Controller).
Click Start, type gpmc.msc in the search box, and press Enter to open the console.
<p>
<img src="https://imgur.com/UOJNILH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
4) Create or Edit a Group Policy Object (GPO)

In the GPMC, navigate to the Group Policy Objects section.
Right-click Group Policy Objects and select New to create a new GPO, or right-click an existing GPO and select Edit to modify it.
If creating a new GPO, give it a descriptive name, such as "Account Lockout Policy."

<p>
<img src="https://imgur.com/ZO7G85K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

5) Navigate to the Account Lockout Policy Settings

In the Group Policy Management Editor, expand:
Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy.

<p>
<img src="https://imgur.com/bpVan6M.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
6) Configure Account Lockout Policy Settings

Adjust the following settings:

a. Account Lockout Duration

Definition: Specifies the time (in minutes) that a locked account remains inaccessible before being automatically unlocked.
Configuration: Double-click the setting, select Define this policy setting, and set the duration (e.g., 30 minutes).


<p>
<img src="https://imgur.com/gYJTnQW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
b. Account Lockout Threshold
Definition: Determines the number of failed login attempts that trigger an account lockout.
Configuration: Double-click the setting, select Define this policy setting, and set the threshold (e.g., 3 invalid attempts).
  
<p>
<img src="https://imgur.com/vGuBAbr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
c. Reset Account Lockout Counter After
Definition: Specifies the time (in minutes) before the failed login attempts counter resets to 0 if no further failed attempts occur.
Configuration: Double-click the setting, select Define this policy setting, and set the time (e.g., 15 minutes).

<p>
<img src="https://imgur.com/undefined.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

7) Force Update Group Policy
- Open the Command Prompt on a client machine or server.
- Type the following command:
- Copy code:
- gpupdate /force  
- Press Enter to execute the command.
**CHANGE THEE PIC. BELOW 
<p>
<img src="https://imgur.com/R37YIbL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

8) Attempt to log in 3 times using an incorrect password.

Verify in Active Directory that the account has been locked out.

<p>
<img src="https://imgur.com/R37YIbL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
