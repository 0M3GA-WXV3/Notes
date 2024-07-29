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

<hr>

### Variables
```$seventyfive = 75```    -    Basic Demonstration

```del variable:(variable name)```      -      Removes a variable

```
$array = "yuh","yuh2","yuh3"
$array | foreach-object{get-alias $_}
```
### Verbage & Basic Commands

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

### Quotation

## '
-  Single quote will make whatever inside it literal, so don't put variable name in here

## "
-  Double quote will interperet whatever is inside it, so putting a variable inside double quote will work properly

