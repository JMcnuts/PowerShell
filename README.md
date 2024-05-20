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



