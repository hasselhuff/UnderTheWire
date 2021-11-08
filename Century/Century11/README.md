# Bandit Level 11 → Level 12

Site: https://underthewire.tech/century-11
## Goal
> The password for Century12 is the name of the hidden file within the contacts, desktop, documents, 
> 
> downloads, favorites, music, or videos folder in the user’s profile.


## NOTE:
> – Exclude “desktop.ini”.
> 
> – The password will be lowercase no matter how it appears on the screen.
-----------------

The following is needed to SSH:
> username: century11
> 
> password: windowsupdates110
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century11 century.underthewire.tech -p 22
```
1. We will build off of previous `Get-ChildItem` commands but include switches to filter our results. We will also use a variable to help shorten the command's length:
```powershell
$userpath = "C:\Users\century11"
(Get-ChildItem -Path $userpath\Contacts,$userpath\Desktop,$userpath\Documents,$userpath\Downloads,$userpath\Favorites,$userpath\Music,$userpath\Videos -File -Hidden -Recurse -ErrorAction SilentlyContinue -Exclude desktop.ini).Name
```
## NOTE:
* We use the `$userpath` variable to specifically specify which root folder to search in since there are many hidden files in `C:\Users\century`, and we can reuse it since all the mentioned folders are in that directory
* `-File` only returns files
* `-Hidden` only returns hidden files
* `-Exclude desktop.ini` since that is a hidden file that can be in either of the above listed directories 
Output:
```powershell
secret_sauce
```
Century12's password is: secret_sauce
