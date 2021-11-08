# Bandit Level 10 → Level 11

Site: https://underthewire.tech/century-10
## Goal
> The password for Century11 is the **10th** and **8th** word of the Windows Update service description 
> 
> combined PLUS the name of the file on the desktop.

## NOTE:
> – The password will be lowercase no matter how it appears on the screen.
> 
> – If the 10th and 8th word of the service description is “apple” and “juice” and the name of the file on the desktop is “88”, 
> 
> the password would be “applejuice88”.
-----------------

The following is needed to SSH:
> username: century10
> 
> password: pierid
> 
> server: century.underthewire.tech
> 
> port: 22

I ssh'ed into the server using:
```bash
ssh -l century10 century.underthewire.tech -p 22
```
1. Since we need the service description we will not be able to use `Get-Service`. Also, since `Get-WMIObject` is becoming obselete we will need to use `Get-CimInstance`
```powershell
Get-CimInstance Win32_Service
```
## NOTE:
* `Win32-Service` is the classname to interact with services with `Get-CimInstance`
2. Now we need to filter the output to only show the `wuauserv` service since that is used for Windows Updates:
```powershell
Get-CimInstance Win32_Service | Where-Object {$_.Name -match "wuauserv"}
```
Output:
```powershell
ProcessId Name     StartMode State   Status ExitCode
--------- ----     --------- -----   ------ --------
0         wuauserv Manual    Stopped OK     0        
```
## NOTE:
* We use `{}` to wrap our filter 
* `$_.Name` is only applying the filter on every result's Name property that is being piped into the `Where-Object`
3. Now to Access the Description property, split each word into it's own line, select only the 10th word, and make that word lowercase:
```powershell
(((Get-CimInstance Win32_Service | Where-Object {$_.Name -match "wuauserv"}).Description).Split(" ")[9]).ToLower()
```
Output:
```powershell
windows
```
4. Now do the same for the for the 8th word by changing the index from 9 to 7:
```powershell
(((Get-CimInstance Win32_Service | Where-Object {$_.Name -match "wuauserv"}).Description).Split(" ")[7]).ToLower()
```
Output:
```powershell
updates
```
5. Now we can string the two commands together as well as utilize the `(Get-ChildItem).Name` from our previous exercise to output the password:
```powershell
(((Get-CimInstance Win32_Service | Where-Object {$_.Name -match "wuauserv"}).Description).Split(" ")[9]).ToLower() + (((Get-CimInstance Win32_Service | Where-Object {$_.Name -match "wuauserv"}).Description).Split(" ")[7]).ToLower() + ((Get-ChildItem).Name).ToLower()
```
Output:
```powershell
windowsupdates110
```

Century11's password is: windowsupdates110
