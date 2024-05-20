# PowerShell

xfreerdp /u:student /v:10.0.. -dynamic-resolution +glyph-cache +clipboard
```
Get-Help *process
```
```
Get-Command -Noun Process
```
```
Get-Command -Verb Start
```
```
Read-Host
```
### Get-Process that start with s:
```
Get-Process s*
```
```
$array = "gal","dir","echo","?"."%","ft"
$array | ForEach-Object{Get-Alias $_}
#Get-NetFirewallRule
#show-retfirewallrule
set-alias gh get-help
gh
```
```
$var1 = Get-Random -Minimum 25 -Maximum 51
$var2 = Get-Random -Minimum 1 -Maximum 10
```
```
$var1 = Get-Random -Minimum 25 -Maximum 51
$var2 = Get-Random -Minimum 1 -Maximum 10
$sum = $var1 + $var2
Write-Host "$var1 + $var2 = $sum"
"{0} + {1} = {2}" -f $var1, $var2, $sum
```
Single quotes will print literally the string, double quotes will print the value of the variable. 
```
$var1 = 10

'$var1'
"$var1"
```
```
$var1 = 10
$var = "Hello, World"
[array]$var[0..5]

'$var1'
"$var1"
```
```
$myblock = { Get-Service | Format-Table Name, Status}
{Get-Service | Format-Table Name, Status}
&$myblock
Invoke-Command $myblock

$a = 1
$b = {1+1}
$a += &$b
Write-Output $a
```
```
Get-ChildItem "C:\Users\student\Desktop" | Sort-Object
```
```
Get-ChildItem | Sort-Object `
-Property Lenght -Descending
```
```
Get-service | Sort-Object status
```
```
Get-process | Group-Object {$_.name.Substring(0,1).ToUpper()}`
 | ForEach-Object{($_.name + " ") *7; "=============";$_.Group}
```
```
1..5 | ForEach-Object {$PSitem+1} #Listing form 1-5

```
```
1..5 | ForEach-Object {$PSitem+1} #Listing form 1-5 +1
```
Array and reverse array in between two random numbers:
```
#Example of a sort descending pre-set array #10, 20, 30 | Sort-Object -Descending 
$var1 = Get-Random -Minimum -10 -Maximum 1
$var2 = Get-Random -Minimum 1 -Maximum 21

Write-Host  
"{0} , {1} " -f $var1, $var2
$var1..$var2 | ForEach-Object {$PSitem} 
$var1..$var2 | ForEach-Object {$PSitem} | Sort-Object -Descending
```
## Practical Exercise: The Pipeline

Display the start time of the earliest and latest running processes

Identify a cmdlet that returns the current date and time then using this cmdlet and Select-object, display only the current day of the week

Identify a cmdlet that displays a list of installed hotfixes.

Extend the expression to sort the list by install date, and display only the install date and hotfix ID.

Extend the expression further, but this time sort by description, include description, hotfix ID, and install Date.

```
Get-Process | Where-Object{$_.starttime} | `
Measure-Object -Property Starttime -Minimum -Maximum |`
Select-Object -Property Minimum, Maximum
```




# Exercises
## Find Cmdlets
```

Update-Help
get-help *process*
get-command -noun process
Get-Service
<# this is
a mulitline
comment #>
$var1 = Read-Host

Write-Output $var1
```
Running Cmdlets
```
Get-Process -ProcessName s*
$array = "gal", "dir", "echo", "?", "%", "ft"
$array | ForEach-Object{Get-Alias $_}
Get-Alias -Name gal
gal -Name dir
gal -Name echo
gal -Name ?
gal -Name %
gal -Name ft
#Get-NetFirewallrule
set-alias gh Get-Help
gh
```
Variables
```
$var1 = Get-Random -Minimum 25 -Maximum 51
$var2 = Get-Random -Minimum 1 -Maximum 11
$sum = $var1 + $var2
$sub = $var1 - $var2
$prod = $var1 * $var2
$quo = $var1 / $var2
Write-Host $var1,+,$var2,=,$sum
Write-Host $var1 "-" $var2 "=" $sub
Write-Host $var1 "*" $var2 "=" $prod
Write-Host $var1 "/" $var2 "=" $quo
"{0} + {1} = {2}" -f $var1, $var2, $sum
Write-Output "test $var2"
```

Variables and Math
```
$var1 = 1
$var2 = 2
$var3 = 3
$var6 = $var1 + $var2 + $var3
$vars = "hello"
[array]$vars[0..4]
$myblock = { get-service | format-table name, status}
&$myblock or invoke-command $myblock (runs the command)
backtick is escape character for word wrap in ISE
sort-object -property * -descending
```

Get-process | group-object {$_.name.substring(0,1).ToUpper()} | foreach-object{($_.name + " ") * 7; "======"; $_.group}


Automatic Variables: $false, $true, $_ (pipeline), $Matches, $input

Typecasting: [string]$var + 'hello', ([string]$var+'hasdf').GetType()

return specific part of table: ([string]$var+'hasdf').GetType().Name

see all properties and methods: | Get-Member
