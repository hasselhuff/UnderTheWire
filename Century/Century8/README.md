# Bandit Level 8 → Level 9

Site: https://underthewire.tech/century-8
## Goal
> The password for Century9 is the number of unique entries within the file on the desktop.

-----------------

The following is needed to SSH:
> username: century8
> 
> password: 7points
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century8 century.underthewire.tech -p 22
```
1. Do a `Get-ChildItem` to list the file on the desktop. Which was `unique.txt`
2. Ran `Get-Content` to read the file, but also sort the output by unique entries and get the count of results:
```powershell
(Get-Content unique.txt | Sort-Object -Unique).count
```
Output:
```powershell
696
```

Century9's password is: 696
