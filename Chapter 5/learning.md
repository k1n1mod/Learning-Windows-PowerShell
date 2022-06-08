By default u are not allowed to run a ps file
Get-ExecutionPolicy
Rectricted
Set-ExecutionPolicy RemoteSigned
cd to the path
u need to path\script.name to run it or .\file.name

# shortcut
- create a shortcut
- right click the shortcut and choose properties
- click on the shortcut tab
- in the target field enter:
  - %SystemRoot%\system32\WindowsPowerShell\v1.0\powershell.exe -ExecutionPolicy Bypass -File "file.name"

# Variables
- $<varable name>
- New-Variable cmdlet
  - Provides parameters that can be used to set the properties of the variable
    - Description
    - Read-only
    - Constant
    - Scope
    - Public or Private

[int]$a=4 locks the $a as an int else u can set $a="Mark"

# Constants
$serverIP='10.10.10.10'
Set-Variable $serverIP -option ReadOnly it protect it for a overwrite
Set-Variable $serverIP -option none -force
Remove-Variable serverIP -force
Set-Variable $serverIP -option Constant -value '12.12.12.12'

# Comparison Operators
-eq =
-lt <
-gt >
-ge >=
-le <=
-ne !=
i to perform case-insensitive by default
e is case sensitive
# if statement
if(codition) {run this code block}
else if
if(codition) {run this code block}
ElseIf(codition) {run this code block}
Else(codition) {run this code block}
# looping
    |for| each-object through a collection of objects|
    |for |number of times|
    |while |until condition remains true|
    |do while| excecutes once, then tests the condition then repeats as long as a condition remains true|
    |do until| executes one and repeats until a condition is true|
# regular expressions
|.(period)| matches a single character|
|[aeiou]| matches at least one character|
|[b-f]| matches at lest one character within a range|
|[^bcdef]| matches any character except those within the brackets|
|^|mateches characters located at the beginning of a string|
|$| matches characters located at the end of a string|
|*| mateches zero or more occurrences of the preceding character|
|?| mateches zero or one occurrences of the preceding character|
|\| matches the character following the escape \ character|
|{n}| must match n times|
|{n,}|must at least n mateches|
|{n,m}| must match at least n times, but not more than m times|
|\d |any decimal 0-9|
|\w| any word character, same as [0-9A-Za-z]|
|\D| any non-digit|
|\W| any non-word character such as space|
|\S| any non-whitespace character|
example
$ssn="111-11-1234"
$rxssn="^\d{3}-\d{2}-\d{4}$"

# escape character and comments
|`|at the end of a command line to continue the command on the next line|
|`$|to include a $ in the output|
|`0|means NULL|
|`a| makes an Alert sound|
|`b|backspace|
|`f|formfeed only affects printed documents|
|`n|new line|
|`r|carriage return|
|`t|horzontal tab|
|`v|vertical tab only affects printed documents|

# parameters with scripts
simple
- Param([string]$variablename)
Full
- Param([Parameter(Mandatory=$ture)][string]$variablename)
Example
```
Param(
    [Parameter(Mandatory=$ture)]
    [string]$variablename
    )
    $a = $username
    Write-Host "Hello $a!"
```