# Bandit Level 7 → Level 8

Site: https://underthewire.tech/century-7
## Goal
> The password for Century8 is in a readme file somewhere within the contacts, desktop, 
> 
> documents, downloads, favorites, music, or videos folder in the user’s profile.

## NOTE:
> – The password will be lowercase no matter how it appears on the screen.
-----------------

The following is needed to SSH:
> username: century7
> 
> password: 197
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century7 century.underthewire.tech -p 22
```
1. Similar to the `find` command on Linux, we will need to set a starting point to begin a recursive search as well as a filter on what we are looking for:
```powershell
(Get-ChildItem -Path C:\users\century7 -Recurse -Filter readme*).FullName
```
## Note:
* Like Linux, the homepath for a user is in the directory named after the user in the user's folder. Where in Linux it would have been `/home/century7` in windows it is `C:\Users\century7`
* I used the `().FullName` in order for my output to only show the full path to the file that matches:
Output:
```powershell
C:\users\century7\Downloads\Readme.txt
```
Output without the `().FullName`:
```powershell
    Directory: C:\users\century7\Downloads                                                                                                                                                                                                                                                                                       Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/30/2018   3:29 AM              7 Readme.txt 
```
2. Now to read the file we use `Get-Content` which is similar to `cat` in Linux (run `alias cat`:
```powershell
Get-Content C:\users\century7\Downloads\Readme.txt
```
Output:
```powershell
7points
```
## BONUS:
We can chain the above two commands in order to simplify the process:
```powershell
Get-ChildItem -Path C:\users\century7 -Recurse -Filter readme* | Get-Content
```
Century8's password is: 7points
