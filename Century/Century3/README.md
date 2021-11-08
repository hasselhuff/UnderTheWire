# Bandit Level 3 → Level 4

Site: https://underthewire.tech/century-3
## Goal
> The password for Century4 is the number of files on the desktop.
-----------------

The following is needed to SSH with the password from the Slack Channel page:
> username: century3
> 
> password: invoke-webrequest443
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century3 century.underthewire.tech -p 22
```
1. Ran the `Get-ChildItem` command and only pulled the count of results it returned:
```powershell
(Get-ChildItem).Count
```
Output:
```powershell
123
```
Century4's password is: 123
