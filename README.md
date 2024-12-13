<p align="center">
<img src="https://i.imgur.com/aMMGyHQ.jpeg" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />

<h1>Preparing Active Directory Infrastructure in Azure</h1>

 ###

<h2>Description</h2>
In this project, I set up two Virtual Machines (VMs): one running Windows Server, configured as a Domain Controller, and the other running Windows 10, acting as a client that joins the domain. In future projects, I will deploy Active Directory (AD), execute scripts to create domain users, log into these accounts from the client VM, manage user accounts, and update group policies. This setup effectively simulates a real-world IT environment!
<br />


<h2>Environments and Utilities Used</h2>

- <b>Microsoft Azure</b>
- <b>Virtual Machines</b>
- <b>Remote Desktop Connection</b>


<h2>Operating Systems Used </h2>

- <b>Windows Server </b>
- <b>Windows 10 Pro</b>

<h2>Project Walk-through:</h2>

  1) Handling Account Lockouts
- Access the DC-1 Server

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

9) Unlock the account in Active Directory.

-   Go to Active Directory Users and Computers > _EMPLOYEES

<p>
<img src="https://imgur.com/ndmJ4n0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
-  Go to the Find function > go type in the username of the person being disabled.
  <p>
<img src="https://imgur.com/XJVQ2QW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Double click on the username and the "Properties" tab should pop up. From, there click "Account". Then checkmark the Unlock account the account is currently loaded out of the Active Directory Domain Controller". & reset the password.
  <p>
<img src="https://imgur.com/R93H7LX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://imgur.com/RRRWkHQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
11) Attempt to log in with the correct password with the client-1 desktop.
results are successful
<p>
<img src="https://imgur.com/gwf8zT9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
12) Enabling and Disabling Accounts
- Disable the Account
- In Active Directory, locate and disable the account.
<p>
<img src="https://imgur.com/PpbSD6B.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://imgur.com/Eayds2f.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://imgur.com/T59sU1z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
14) Try logging in with the disabled account and note the error message displayed.
Re-enable the Account
<p>
<img src="https://imgur.com/gEcLHFM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
15) In Active Directory, re-enable the account.
Attempt to Log In Again
<p>
<p>
<img src="https://imgur.com/ehGoVUD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://imgur.com/e4zokvv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Log in using the re-enabled account to confirm successful access.
<p>
<p>
<img src="https://imgur.com/8lmLetj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

16) Check Logs on the Domain Controller

- Open Event Viewer on the Domain Controller as Admin using Jane cridentails.
<p>
<p>
<img src="https://imgur.com/qZnjaHr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
- Navigate to Windows Logs > Security to review login attempts, account lockouts, and related security events.
<p>
<p>
<img src="https://imgur.com/qZnjaHr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
- Check Logs on the Client Machine
Open Event Viewer on the client machine.
Navigate to Windows Logs > Security to review failed login attempts and any associated error messages.

<p>
<p>
<img src="https://imgur.com/BSQdlle.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
