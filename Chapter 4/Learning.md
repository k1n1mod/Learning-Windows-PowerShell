# Cmdlets are designed to have similar structure and syntax
- They utilize the same basic structure
  - Verb - Noun -parameter argument
  - The verv describes the action that is to take place
  - The noun describes the target of that action
  - The parameter is an optional characteristic or property of the noun
    - PS parameters are always precceded by a hypjen (-)
  - The argument is a value that can be providet for a parameter

# Cmdlets Verb
There are six common cmdlets verbs
- Get
- Set
- Enable
- Disable
- New
- Remove
Other verbs
Add, Clear, Export, Format, Import, Invoke

# Get-Help
one page
    help <cmdlet>
multi pages
    <cmdlet> -?
examples
    Get-Help <cmdlet> -examples
more information
    Get-help <cmdlet> -detailed
New window with search
    Get-Help Get-Process -ShowWindow

# Format
    - Wide
    - List
    - Table
    - Custom

# Members

$m = "Hello there!"
$m | Get-Memer
$m.Length
$m.ToUpper()
$m | Get-Member -membertye properties

# NET Objects
- Create a variavle $m and loaded "Hello There!" into it
- The variable it became a string object
- .NET string objects have certain methods and properties
- Get-Member provided a list of those properties and methods
  - When PS made $m a string-based variavle, it acquired all the capabilities of a .NET string object

# Objects an Classes

 - .NET Framework Classes
 - Objects
 - PS commands
## .NET Framework Classes
is a bunch of classes that define objects, the same way a blueprint defines houses
houses (objects) are constructed based on the blueprint (class)
## Objects
Are created in memory based on a particular class
the string object has whatever functionalities are defined in the Sting class
## PS commands
You can utilize the properties and methods of these objects to create powerful functionalities

MLCLass.dll
[Reflection.Assembly]::LoadFile("Path\MLClass.dll")
$ml = new-object MLClass.Messages
$ml.SendMsg()
$ml | Get-Member

# Get-ChildItem
refer by its built-in aliases
    ls
    dir
    gci
In the folder to show all the other paths
```
Get-ChildItem -recurse
```
to find for example a .txt file
gci c:\*.* -include *.txt

# Pipeline
$_ use to check the current status of the current contents of the pipeline at the particular point in time
Get-Service | Where-Object {$_.DisplayName -match "MS"}

# Tab Completion
*-S complete all the stuff what starts with a s behind the -