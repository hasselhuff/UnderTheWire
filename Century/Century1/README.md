# Bandit Level 0 → Level 1

Site: https://underthewire.tech/century
## Goal
> The goal of this level is to log into the game. Do the following in order to achieve this goal.
> 
> 1. Obtain the initial credentials via the #StartHere channel on our Slack (link). Once you are in the channel, scroll to top to see the credentials.
> 
> 2. After obtaining the credentials, connect to the server via SSH. You will need a SSH client such as Putty. 
> The host that you will be connecting to is century.underthewire.tech, on port 22.
> 
> 3. When prompted, use the credentials for the applicable game found in the #StartHere Slack channel.
> 
> 4. You have successfully connected to the game server when your path changes to “PS C:\Users\Century1\desktop>”.
-----------------

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





