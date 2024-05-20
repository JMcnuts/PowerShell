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
Practical Exercise: The Pipeline
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
