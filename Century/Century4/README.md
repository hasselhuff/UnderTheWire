# Bandit Level 4 → Level 5

Site: https://underthewire.tech/century-4
## Goal
> The password for Century5 is the name of the file within a directory on the desktop that has spaces in its name.

## NOTE:
> – The password will be lowercase no matter how it appears on the screen.
-----------------

The following is needed to SSH:
> username: century4
> 
> password: 123
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century4 century.underthewire.tech -p 22
```
1. Ran the `Get-ChildItem` to list contents of the desktop directory:
```powershell
Get-ChildItem
```
Output:
```powershell
    Directory: C:\users\century4\desktop

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/3/2021   1:15 AM                Can You Open Me
d-----         3/2/2021   6:57 PM                One      Directory
d-----         7/3/2021   1:17 AM                Open              Me
d-----        3/14/2021   9:11 PM                Open     Me
-a----         7/9/2021   6:07 PM            272 file.txt
-a----        8/24/2021  12:17 AM           1486 files.txt
```
2. Ran `Get-ChildItem` on `Can You Open Me` but wrapped the file name with `'` to escape the spaces and make the sentence a string. I wrapped the entire command with `().Name` to ouput only the `Name` attribute:
```powershell
(Get-ChildItem 'Can You Open Me').Name
```
Output:
```powershell
61580
```

Century5's password is: 61580
