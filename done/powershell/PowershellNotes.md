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

### Math (Square Root, Exponents)

```[math]::sqrt(64)```

```[math]::pow(6,2)```

### Searching
   -   Where-Object
```'msedge' -like '*MS*'```

```'msedge' -clike '*MS*'```

```'msedge' -like '*MS*'```

### Averaging
   -   Averaging properties
1,2,3,4,5 | Measure-Object -Average

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
   -   A RegEx pattern matching to a string 
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
   -    Iterate through until string matches what it wants
```
$var = ""
while($var -ne "Marin Crops"){
   $var = read-host "Best Brnache?"
}
```
   -    Iterate through until number is reached
```
$num = 0
do {
   $num
   $num++
}until($num -eq 101)
```

## For Loop
   -    Basic For Loop
```
for($num = 1; $num -le 3; $num++){$num}
```
   -   Display IP range for 
```
for($i = 0; $i -le 255; $i++) {
   write-host 192.168.0.$i}
```
   -   Use of Break & Continue
* Break
```
$num = 0
while($num -lt 10) {
   $num += 1
   if($num -eq 2) {
   break
    }
    $num
}
```
* Continue
```
$num = 0
while($num -lt 10) {
   $num += 1
   if($num -eq 2) {
   continue
    }
    $num
}
```

## Add, Set, and Get content
```set-content -path ./example.txt -value "string desired"```

```get-content ./example.txt```

```add-content ./example.txt -value "When my homie says, On Crud? I just say, On crud on BLUD!"```

## Starting and Stopping processing using arrays
* Starting
```
$array = "notepad", "msedge", "mspaint"
$array | ForEach-Object { Start-Process $_ }
```
* Stopping
```
$array = "notepad", "msedge", "mspaint"
$array | ForEach-Object { Stop-Process -name $_ }
```

### showing info on programs
```
$array = "notepad"
foreach($array in $array){
get-process | where-object{$_.Name -like $array} | format-table -property id, name, starttime, totalprocessortime, virtualmemorysize, workingset64
}
```

# Day3 

## Functions (Kinda retarded)

   -   Input being ranked and sorted based on character count
```
function get-longestname{
    Begin{
        $count = 0
        $states = @()
        }
        Process{
            while($count -lt 3){
                $usr = Read-Host "Enter a word"
                $states += $usr
                $count += 1
            }
        }
        End{
            $list = $states | sort -Property length -Descending
            forEach($i in $list){
                "$i`: " + $i.length
            }
        }
}
```
   -   Get Netowrking Information
```
Function get-netinfo {
    $pattern = '.*?((\d{1,3}\.){3}\d{1,3})'
    $netinfo = ipconfig
        $ip = $netinfo -match "IPV4$pattern" | `
        %{if($_ -match $pattern){$Matches[1]}}
        $subnet = $netinfo -match "Subnet$pattern" | `
        %{if($_ -match $pattern){$Matches[1]}}
        $gate = $netinfo -match "Gateway$pattern" | `
        %{if($_ -match $pattern){$Matches[1]}}
    "IP: {0}`nSubnet: {1} `nGateway: {2}" -f $ip,$subnet,$gate
}
```
   -   Get URLs from a file
```
Function get-urlinfo {
    $file = Get-Content .\dns.txt
    $regex = '([a-zA-Z0-9\-\.]+\.(com|net|org))'
    foreach($line in $file) {
        if($line -match $regex) {
            $Matches[1]
        }
    }
}
```

## Split and Join
