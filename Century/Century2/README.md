# Bandit Level 2 → Level 3

Site: https://underthewire.tech/century-2
## Goal
> The password for Century3 is the name of the built-in cmdlet that performs the wget like function within 
> 
> PowerShell PLUS the name of the file on the desktop.

## NOTE:
> – If the name of the cmdlet is “get-web” and the file on the desktop is named “1234”, the password would be “get-web1234”.
> 
> – The password will be lowercase no matter how it appears on the screen.
-----------------

The following is needed to SSH with the password from the Slack Channel page:
> username: century2
> 
> password: 10.0.14393.4467
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century2 century.underthewire.tech -p 22
```
1. Ran the `alias` command with `wget` to see if there was a built-in alias:
```powershell
alias wget
```
Output:
```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           wget -> Invoke-WebRequest
```
2. Now to list the file on the user's Desktop:
```powershell
Get-ChildItem
```
Output:
```powershell
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/30/2018   3:29 AM            693 443
```
## BONUS:
1. For the `Get-ChildItem` we can limit the output to only show file names:
```powershell
(Get-ChildItem).Name
```
Output:
```powershell
443
```

Century3's password is: invoke-webrequest443
