# Bandit Level 5 → Level 6

Site: https://underthewire.tech/century-5
## Goal
> The password for Century6 is the short name of the domain in which this system resides in PLUS the name of the file on the desktop.

## NOTE:
> – If the short name of the domain is “blob” and the file on the desktop is named “1234”, the password would be “blob1234”.
> 
> – The password will be lowercase no matter how it appears on the screen.
-----------------

The following is needed to SSH with the password from the Slack Channel page:
> username: century5
> 
> password: 61580
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century5 century.underthewire.tech -p 22
```
1. Ran the environmental variable `$env:USERDOMAIN` to get the short name of the domain:
```powershell
Get-ChildItem
```
Output:
```powershell
underthewire
```
2. Then to get the file name on the desktop:
```powershell
(Get-ChildItem).Name
```
Output:
```powershell
3347
````
## BONUS:
We can chain both commands to output the password in one command:
```powershell
$env:USERDOMAIN + (Get-ChildItem).Name
```
Since the output of both are strings we can use the `+` to append the outputs together
Output
```powershell
underthewire3347
```

Century6's password is: underthewire3347
