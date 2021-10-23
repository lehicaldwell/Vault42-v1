# Vault42
A personal or service user vault for storing and accessing credentials. Currently, it is limited to PowerShell use only, but I do intend to write a python GUI for it in the future.
Download the current documentation here :

- Initialize-Vault42.ps1 : This was created to make intial configuration as easy as possible. The intent is to have the Vault42.zip file pulled down, then the Initialize-Vault.ps1 script. Then, the user runs Initialize-Vault42 as admin, and the script will get everything in place to be used. The next step is to run the New-Vault.ps1 command to configure the vault.

- New-Vault.ps1 : This script walks the user through getting a vault configured. The 2 acceptable arguments for -VaultType are Service or User. Service vaults are static in configuration due to the methodic nature of service accounts, where User vaults are more flexible. If the vault is created for a user, it is recommended that they user Start-Vault42.ps1 as opposed to Get-ServiceCreds.ps1.

- Get-ServiceCreds.ps1 : This script is intended to access the service vault to get credentials in an automated fashion. The script has 2 mandatory parameters. 
     1 -AccountName ; this should match the account name given to the vault that has the credentials desired.
     2 -AuthTarget ; This is more arbitrary, as it can be something such as LAN, the URL, or a Server name.
            Again, this is used for distinguishing the credentials you want to use.
