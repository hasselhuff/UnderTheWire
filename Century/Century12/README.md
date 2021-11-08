# Bandit Level 12 → Level 13

Site: https://underthewire.tech/century-12
## Goal
> The password for Century13 is the description of the computer designated as a Domain Controller 
> 
> within this domain PLUS the name of the file on the desktop.


## NOTE:
> – The password will be lowercase no matter how it appears on the screen.
> 
> – If the description “today_is” and the file on the desktop is named “_cool”, the password would be “today_is_cool”.
-----------------

The following is needed to SSH:
> username: century12
> 
> password: secret_sauce
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century12 century.underthewire.tech -p 22
```
1. Get the name of the Domain Controller:
```powershell
(Get-ADDomainController).Name
```
Output:
```powershell
UTW
```
2. Now get the description of the Domain controller `UTW`:
```powershell
(Get-ADComputer utw -Properties Description).Description
```
## NOTE:
* We add `-Properties Description` since that is not a default value that `Get-ADComputer` displays 
Output:
```powershell
i_authenticate
```
3. Now chain the above command with the our previous `Get-ChildItem` commands:
```powershell
(Get-ADComputer utw -Properties Description).Description + (Get-ChildItem).Name
```
Output:
```powershell
i_authenticate_things
```
Century13's password is: i_authenticate_things
