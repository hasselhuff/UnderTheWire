# Bandit Level 9 → Level 10

Site: https://underthewire.tech/century-9
## Goal
> The password for Century10 is the 161st word within the file on the desktop.

## NOTE:
> – The password will be lowercase no matter how it appears on the screen.
-----------------

The following is needed to SSH:
> username: century9
> 
> password: 696
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century9 century.underthewire.tech -p 22
```
1. Do a `Get-ChildItem` to list the file on the desktop. Which was `Word_File.txt`
2. Ran `Get-Content` to read the file, but also split the words in each line to their own line in order to find the 161st word by indexing:
```powershell
(Get-Content Word_File.txt).Split(" ")[160]
```
## NOTE:
* `().Split(" ")` says to take the output and create a newline for every space
* `[160]` is selecting the 161st index of the output (since computers start counting with 0 rather than 1)
>
Output:
```powershell
pierid
```

Century10's password is: pierid
