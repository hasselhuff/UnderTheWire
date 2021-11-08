# Bandit Level 6 → Level 7

Site: https://underthewire.tech/century-6
## Goal
> The password for Century7 is the number of folders on the desktop.
-----------------

The following is needed to SSH:
> username: century6
> 
> password: underthewire3347
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century6 century.underthewire.tech -p 22
```
1. Similar to retrieiving all files, we will use `Get-ChildItem` but specify only folders/ directories:
```powershell
(Get-ChildItem -Directory).count
```
Output:
```powershell
197
```

Century7's password is: 197
