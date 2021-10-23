# Vault42
A personal or service user vault for storing and accessing credentials. Currently, it is limited to PowerShell use only, but I do intend to write a python GUI for it in the future. The idea behind this is to make a tool that is local to the device only and does not reside on outside resources. So if you're like me and skeptical of all things online, this may be a decent alternative to browser based password managers. 
Download the current documentation here :

- Initialize-Vault42.ps1 : This was created to make intial configuration as easy as possible. The intent is to have the Vault42.zip file pulled down, then the Initialize-Vault.ps1 script. Then, the user runs Initialize-Vault42 as admin, and the script will get everything in place to be used. The next step is to run the New-Vault.ps1 command to configure the vault.

- New-Vault.ps1 : This script walks the user through getting a vault configured. The 2 acceptable arguments for -VaultType are Service or User. Service vaults are static in configuration due to the methodic nature of service accounts, where User vaults are more flexible. If the vault is created for a user, it is recommended that they user Start-Vault42.ps1 as opposed to Get-ServiceCreds.ps1.

- Start-Vault42.ps1 : This is an infinite loop (unless you enter the quit command), that will allow you to access and manage the vault. This is intended to be used with an interactive login session, hence the infinite loop. Just open a PowerShell prompt, run the command, and viola, an infinite loop to access the credentials stored there-in. Features include : 
    1 - add : This walks the user through adding a new credential set to the vault. 
    2 - set : Used to change a password/key value
    3 - rem : Used to remove a credential set. * THERE IS NO WAY OF RESTORING REMOVED CREDENTIALS *
          Yes, this is intentional. I will not alter this in an effort to prevent accidental leakage or theft.
    4 - get : used to get the plaintext version of the account requested. The screen will clear after you 
              press enter, and the plaintext version is lost to the ether. You cannot scroll up, it does not
              show in history. 

- Get-ServiceCreds.ps1 : This script is intended to access the service vault to get credentials in an automated fashion. The script has 2 mandatory parameters. 
     1 -AccountName ; this should match the account name given to the vault that has the credentials desired.
     2 -AuthTarget ; This is more arbitrary, as it can be something such as LAN, the URL, or a Server name.
            Again, this is used for distinguishing the credentials you want to use.
      Note : Consideration is being given to add in a parameter for description for further dichotomy of accounts.
          EX. ServiceAccountA name/email is used in 5 different websites, and 3 different computers, for 4 
          different resources/apps. Adding description field would allow the same name to be used, the same target, 
          but target a different resource, using different credentials. 
