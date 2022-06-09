# Provider
- alias
- environment
- filesystem
- function
- registry
- variable
- certificate
- wsman

Get-PSProvider
Get-PSDrives
set-location alias:

Create my own psdrive 
new-psdrive -name mldocs -PSProvider filesystem -Roor (resolve-path ~/*documents)
set-location mldocs:

Once you move to a PSDrive provided by one of the providers
You utilize the same PowerShell commands and their parameters to perform familiar tasks
- Get-Location - Rename-Item
- Set-Location - Set-Item
- New-Item - Clear-Item
- Copy-Item - Etc.

# FileSystem Provider

Part of the date provided by the FileSystem provider is the mode column
|Column 1 |"d"| indicates item is a directory |"-" |indicates item is a file|
|Column 2|"a"|indicates the archive bit is set|||
|Column 3|"r"|indicates read-only|||
|Column 4|"h"|indicates hidden|||
|Column 5|"s"|indicates system|||

set-location windows || cd c:\ 
get-childitem -force //see all hidden and system files

# Alias Provider

Alias is another name assigned to a cmdlet
Mount a PSDrive to access the Alias provider

Set-Location Alias:
Get-ChildItem -Name c*
New-Alias ml Get-ChildItem

!Alias stay only for one session if u want to keep this save it in your ps profil

# Variable and Function Provider 
Variable Provider shows us which PS and user defined variables are available
PS variables are preceded by the dollar sign character ($)
However, the list of variables in the Variable Provider do not include the $ as the first character
Just add the $ to access the variables in PowerShell code and scripts

set-location variavle: 
dir

function a named block of code
PS has a set of functions built-in

set-location function: 
gci

Get-Content clear-host //shows the content of the function

# Environment Provider
exposes all the environment variables defined on the system

set-location env:
gci 
Get-ChildItem os  | Format-List * 

# Registry Provider
Navigate and manage the registry the same way u navigate and manage the file system
 -  Navigate the registry
 -  Search the registry
 -  Create new keys
 -  Add new values
 -  Modify existing values
 -  Manage ACLs (Access Control Lists)

exposes two PSDrivers HKCU || HKLM

set-location HKLM:\Software
gci

# Certificate Provider
The Certificate Provider is not automatically imported into every session

set-location cert:
gci -path cert:\LocalMAchine

Get-ChildItem -recurse | Export-CSV "C:\MLCerts.csv"
invoke-item "C:\MLCerts.csv"