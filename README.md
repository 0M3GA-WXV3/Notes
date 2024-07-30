# Day 1

<hr>

## RDP

WINDOWS:
10.50.24.165

LINUX:
10.50.35.203
```
xfreerdp /u:student /v:10.50.24.165 -dynamic-resolution +glyph-cache +clipboard
```
## Links

https://ss64.com/ps/

https://cted.cybbh.io/tech-college/pns/public/pns/latest/powershell/pe_running_cmdlets.html

https://red-gate.com/simple-talk/sysadmin/powershell/when-to-quote-in-powershell

https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7.4

https://www.tutorialspoint.com/powershell/powershell_brackets.htm



<hr>

## Variables
```$seventyfive = 75```    -    Basic Demonstration

```del variable:(variable name)```      -      Removes a variable

```
$array = "yuh","uhuh2","ahah3"
$array | foreach-object{get-alias $_}
```
## Verbage & Basic Commands

```get-help (command/*log*) (-Examples/-full/-online)```    -      Shows info on command, find commands with word in apostraphes, and show examples/full documentation

```get-command (-verb/-noun) get/process```    -   Displays all commands, options for starting with word "get", or all commands ending in "process"

```get-process```    -    Shows all running processes and associated data

```get-childitem (-path) (-filter *.exe) (-recurse) (-name)```    -      Shows everything in a given directory, with or without a filter

```get-alias (-Definition) (commands)```      -      retreives attached alias'

```set-alias (edit) (executable file)```      -      Makes new alias referring to set executable

```remove-item (alias):(name of alias) ```      -     Removes an alias

```(get-process).id.processname```
```(getprocess notepad).kill()```     -      Using parentheses and period between the portions of a command's output, can specify field displayed

```get-process | get-member -membertype properties```      -      Show fields of command

```get-service | ft name, status```      -      Show specific portions of command in format table
```get-service | where-object -property status -eq 'Stopeed' ```

## Quotation

### '
-  Single quote will make whatever inside it literal, so don't put variable name in here

### "
-  Double quote will interperet whatever is inside it, so putting a variable inside double quote will work properly

## Format
```"{0} + {1} = (2)" -f $sum```    -    Will make what is in quotes the format for which to put the variables out

## Sequence

``` $reversearray = -3..15; $reverse = $reversearray[($reversearray.length-1)..0]```  -  Creates a reverse array

### Setting fields on a variable
```
$employee1 = [ordered]@{}
$employee2 = [ordered]@{}

$employee1.First = "Mick"
$employee1.Last = "Mundee"
$employee1.ID = "008"
$employee1["Job"] = "A Professional"
$employee1

$employee2.First = "Jane"
$employee2.Last = "Doe"
$employee2.ID = "002"
$employee2["Job"] = "A Soldier"
$employee2
```

# Day 2

## Command Substitution
   -    Example of command substitution in powershell, invoke-command (&) denotes to run the following function
```
$myblock = {get-service | format-table name, status}
& $myblock
```
## Sorting & Grouping

```get-childitem | sort-object (-property) lengeth (-descending)```     -    Sorting fetched items by the property of length

```get-childitem C:\ | group-object {$_.length -lt 1kb}```    -    Grouping items by file size

```get-process | select-object (-last/-first) 10```    -    Selecting first or last 10 entries of processes, similar to head/tail

```get-process | select-object -ExpandProperty name```    -    Sorts by certain field

```get-process | where-object {$_.company -like 'micro*'} | format-table Directory, name, length```     -    Sorts the different objects to find anything with company info attached from companies starting with "micro"

```get-process | where-object {$_.name -notlike 'powershell*'} | sort-object id -Descending```     -    Returns every object, sorted by ID if it is not a powershell instance

```get-process | where-object processname -ne "Idle" | sort-object starttime | select-object -last 10 | format-table processname, starttime | 2>$null```      -      Returns all objects 

## Array piping

Array objects being piped into code block, allowing iteration of foreach to add array objects together
```
$array = 1,2,3,4,5
$sum = 0
$array | foreach-object {$sum += $_}
$sum
```

## Objects
   -    Creating a New Object
```
$MyTruck = new-object object
```
   -    Adding new values to the Object
```
Add-Member -MemberType NoteProperty -Name Color -Value White -InputObject $MyTruck
```
```
Add-Member -Me NoteProperty -in $MyTruck -Na Make -Value Toyotas
```
```
Add-Member -InputObject $MyTruck NoteProperty Model "Camry"
```
```
$MyTruck | Add-Member ScriptMethod Parking {"Found a spot under a tree"}
```

## RegEx
A RegEx pattern matching to a string 
```
$text = "Username is GOAT445"
$pattern = '([A-T]{4})(\d{3})'
$text -match $pattern
```

## If else
```
$x = 4
if ($x -eq 5) {
   write-host "Yeah"
}
elseif ($x -eq 4) {
   write-host "Nah"
}
elseif ($x -eq 2) {
   write-host "Maybe"
}
elseif ($x -gt 6) {
   write-host "Nah"
}
else {
   write-host "Who am I?"
}
```

## For Each
   -   Iteration through list of numbers
```
$nums = 1,2,3,4,5
$num | foreach-object{$_ * 2}
```
   -   Iteration through list of strings
```
$list = 'a', 'b', 'c', 'd', 'e'
$list | ForEach-Object {$_.toupper()}
```
   -   Inserting string between list iteration
```
$cars = "DeLorean", "Corvette", "Lexus", "Tesla"
foreach($cars in $cars){"Stupid ass $cars"}
```
   -   Uppercasing every process listed
```
get-process | ForEach-Object {$_.Name} | ForEach-Object {$_.toupper()}
```
   -   Lists every file in Directory "C:"
```
ForEach ($item in gci C: -recurse){$item.name}
```

## While Loop
$var = ""
while($var -ne "Marin Crops"){
   $var = read-host "Best Brnache?"
}
