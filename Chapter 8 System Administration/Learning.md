# System Administration
## Workring with processes
PS provides the Get-Process cmdlet for managing the processes on a computer
cmdlets
 - Start_Process
 - Stop-Process
 - Wait-Process
   - Waits for one or more processes to be stopped before accepting input
 - Debug-Process

get-process | where-object {$_.WorkingSet -gt 50000000}
start-process notepad
get-process
stop-process 1092 // enter processID for stopping it
