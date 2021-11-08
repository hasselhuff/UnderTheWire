# Bandit Level 14 → Level 15

Site: https://underthewire.tech/century-14
## Goal
> The password for Century15 is the number of times the word “polo” appears within the file on the desktop.

## NOTE:
> – You should count the instances of the whole word only..
-----------------

The following is needed to SSH:
> username: century14
> 
> password: 755
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century14 century.underthewire.tech -p 22
```
1. Read the file:
```powershell
Get-ChildItem | Get-Content
```
2. Noticed all words are in sentences so we will split them into individual lines and then filter for `polo` and count the results:
Output:
```powershell
((Get-ChildItem | Get-Content).Split(" ") | Where-Object {$_ -like "polo"}).Count
```
## NOTE:
* We use `-like` because we want exact matches, if we had used `-match` words like `waterpolo` would have been in the results
Output:
```powershell
153
```

Century15's password is: 153
