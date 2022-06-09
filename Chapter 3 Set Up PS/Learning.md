Start PS as admin
```
Start-Process Powershell -verb runas
```
PS help files
```
update-help
```
ExecutionPolicy
```
Set-ExecutionPolicy RemoteSigned
```
PS remoting
```
Enable-PSRemoting
```
PS Profil
CurrentUserCurrentHost
%UserProfile%\My Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
VS
%UserProfile%\Documents\PowerShell\Microsoft.VSCode_profile.ps1
create a text file in directory
New-Item -path $profile -Type file -Force