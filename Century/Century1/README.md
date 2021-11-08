# Bandit Level 1 → Level 2

Site: https://underthewire.tech/century-1
## Goal
> The password for Century2 is the build version of the instance of PowerShell installed on this system.

## NOTE:
> – The format is as follows: **.*.*****.****
> 
> – Include all periods
> 
> – Be sure to look for build version and NOT PowerShell version

## IMPORTANT:
> Once you feel you have completed the Century1 challenge, start a new connection to the server, 
> 
> and log in with the username of Century2 and this password will be the answer from Century1. 
> 
> If successful, close out the Century1 connection and begin to solve the Century2 challenge. 
> 
> This concept is repeated over and over until you reach the end of the game.
-----------------
After you read the starting page at [Century](https://underthewire.tech/century)
The following is needed to SSH with the password from the Slack Channel page:
> username: century1
> 
> password: century1
> 
> server: century.underthewire.tech
> 
> port: 22

## NOTE:
> PowerShell version `5.1.22000.282` or later on Windows 10 supports the `ssh` command (the shell may become distorted)
> 
> You may also use Putty or ssh from a Linux distribution

I ssh'ed into the server using:
```bash
ssh -l century1 century.underthewire.tech -p 22
```
1. Ran the global variable for the details of the installed PowerShell version:
```powershell
$PSVersionTable
```
2. The above gave this output:
```powershell
Name                           Value
----                           -----
PSVersion                      5.1.14393.4467
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.14393.4467
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Century2's password is: 10.0.14393.4467
