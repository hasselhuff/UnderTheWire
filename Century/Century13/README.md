# Bandit Level 13 → Level 14

Site: https://underthewire.tech/century-13
## Goal
> The password for Century14 is the number of words within the file on the desktop.

-----------------

The following is needed to SSH:
> username: century13
> 
> password: i_authenticate_things
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century13 century.underthewire.tech -p 22
```
1. Read the file:
```powershell
Get-ChildItem | Get-Content
```
2. Noticed all the words are in sentences so we will need to split each word into their own line and then count the total lines:
```powershell
((Get-ChildItem | Get-Content).Split(" ")).Count
```
Output:
```powershell
755
```
Century14's password is: 755
