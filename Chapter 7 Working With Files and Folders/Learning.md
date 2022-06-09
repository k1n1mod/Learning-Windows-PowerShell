# Files and Folders
PS make managing files and folders easy
it also privides the abiility to get a lot of info about the files and folders 
such tasks as
 - Listing all the files and folders within a folder
 - Find specific files based on last modified date
 - Find files in specified folders based on last modified date
 - copy a folder and its contents

gci shows item gci -force show hidden items

Searching for last modified date
Get-ChildItem -Path "C:\Program Files" -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt "2022-06-01")}

use FindFiles.ps1

set-location c:\
.\FindFiles.ps1
Path <- Where should it search
LastWrite: <- And it shows the on which day example 09-01-22

# Reading and write
PS provides a number of ways to wirte data to files
By using the > redirection operator
By using the Set-Content cmdlet
    Set-Content cmdlet will overwrite and replace data already in the file
    The Add-Content cmdlet will append data to a file
Piping data to the Out-File cmdlet

```
new-item c:\newitemtest.txt -type file
Set-Content c:\newitemtest.txt "It was the worst of times..." 
// notice Set.Content alway overwrite the file
Add-Content c:\newitemtest.txt "It was the best of times..." 3
// Add content to the file
gci | Out-File c:\mltest.txt

get-content c:\mltest.txt
```

# Output HTML
making data easily accessible to large numbers of people
PS provides the COnvertTo-HTML cmdlet just pipe date to the ConvertTo-HTML cmdlet

Export Runnign Services to a HTML file
get-service | where-object {$_.status -eq "running"} | ConvertTo-HTML Name, DisplayName, Status | Set-Content C:\svc.html

# Output to xml
Create XML
gci | Export-Clixml C:\XMLtest.xml   //to create xml file from Get-ChildItem
Read XML
$x = Import-Clixml C:\XMLtest.xml   //load xml data into variable
$x

# Working with CSV
comma separated values

Write data to csv
Get-Service
Get-Service | Export-CSV C:\SvcList.csv

Import data from csv
$s = Import-CSV C:\SvcList.csv
Or
Invoke-Item C:\SvcList.csv


