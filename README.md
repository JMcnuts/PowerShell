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

## Comparison and Condition :
```
$line1 = "Do you have model number: MT5437 for john.doe@sharklasers.com?"
$line2 = "What model number for john.doe@sharklasers.com?"

    $line1 -replace '\D+([0-9]*).*','$1' 
     if ($line1 -replace '\D+([0-9]*).*','$1' -le 0)
     {
     Write-Output "Model number wasn't found for line 1"
     }
     else 
     {
     Write-Output "Is the model number for line 1"
     }

     $line2 -replace '\D+([0-9]*).*','$1' 
     if ($line2 -replace '\D+([0-9]*).*','$1' -le 0) 
     {
     Write-Output "Model number wasn't found for line 2"
     }
     else 
     {
     Write-Output "Is the model number for line 2"
     }
```
```
$line1 = "Do you have model number: MT5437 for john.doe@sharklasers.com?"
$line2 = "What model number for john.doe@sharklasers.com?"

$pattern = "[A-Z]{2}[0-9]{4}"
$line1,$line2 | ForEach-Object  {
        if($_ -match $pattern) {
            Write-Host $Matches[0]": $_"
        }
            else{
            Write-Host "No matches found on : $_"
         }
    }
     'MT5437' -match '[A-Z]{2}[0-9]{4}'
     $Matches
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
## If statements :
```
$x = 0
if ($x -eq 5) {
    Write-Host "Bob"
    }
elseif ($x -eq 4) {
    Write-Host "Sue"
    }
elseif ($x -eq 2) {
    Write-Host "Tom"
    }
elseif ($x -eq 1) {
    Write-Host "Mary"
    }
else {
    Write-Host "Who am I ?"
    }

```
```
$BB = "Mr. Krabs", "Sandy", "SpOnge bOb", "Patrick","Larry the Lobster","Plankton","Gary"

foreach($fish in $BB){$fish.tolower()}
foreach($fish in $BB){$fish.toupper()}

foreach($fish in $BB){
    if ($fish -like 'SPONGE*'){
        "$fish is the best fry cook"
        }
        elseif($fish -like '*lob' ){
        "$fish has the most gains"
        }
        else{
        "$fish  is a fine citizen"
        }
        }
```
## Magic Number
```
  $num = [int]0 
        $magic = [int]182
        while ($True){
            $num = [int](Read-Host -Prompt " Pick a number betweek 0 and 200")
            if ($num -lt $magic){
                "Too low!"
                }
            elseif($num -gt $magic){
                "Too high!"
                }
            else {
             "blink -$magic" ; break
             }
            }
```

```
$ray = "notepad", "msedge", "mspaint"
Remove-Item -path pwd\user.txt
$ray | ForEach-Object{start-process $_}
$ray | ForEach-Object{(get-process $_).id | Out-File -append -FilePath pwd\user.txt}
Get-Content -Path $pwd\user.txt | ForEach-Object{stop-process -id $_}
Get-process | group-object {$_.name.substring(0,1).ToUpper()} | foreach-object{($_.name + " ") * 7; "======"; $_.group}

```
or
```
<#Query the processes and display only the following information in order by process ID

Process ID

Process Name

The time the process started

The amount of time the process has spent on the processor

The amount of memory assigned to the process#>

$procs = "notepad", "msedge", "mspaint"
$procs | ForEach-Object { Start-Process $_} 
$procs | ForEach-Object { Stop-Process -name $_}

$file = "$pwd\procs.txt"
$procs | ForEach-Object { Start-Process $_ }
foreach($proc in $procs){
    Get-Process | Where-Object{$_.Name -like $proc} | `
    ForEach-Object { Add-Content $file $_.Id}}
Get-Content .\procs.txt | ForEach-Object{Stop-Process $_}

foreach($proc in $procs){
    Get-Process | Where-Object{$_.Name -like $proc} | `
    Format-Table -Property id, name, starttime, totalprocessortime, `
    VirtualMemorySize, WorkingSet64 }

foreach($proc in $procs){
    Get-Process $proc | `
    Format-Table -Property id, name, starttime, totalprocessortime, `
    VirtualMemorySize, WorkingSet64 }

$procs | ForEach-Object { Get-Process $_ | select id, name, starttime, `
totalprocessortime, VirtualMemorySize, WorkingSet64 | Format-Table }

```

## IPV4 OCTECT VALIDATION

```
foreach ($oct in ('2.3.2.4' -split '\.')) { 
    if ([int]$oct -lt 0 -or [int]$oct -gt 255){
        "$oct is not a valid octect"
    }
    else {"$oct is a valid octet"}
    }
```
## OR
```
('2.3.2.3' -split '\.') | ForEach-Object{
    if([int]$_ -lt 0 -or [int]$_ -gt 255){
    "$_is not a valid octect"
    }
      else {"$oct is a valid octet"}
    }
    'cat','dog' -join "."
    'cat'.StartsWith('c')
    'dog'.EndsWith('t')
```











Automatic Variables: $false, $true, $_ (pipeline), $Matches, $input

Typecasting: [string]$var + 'hello', ([string]$var+'hasdf').GetType()

return specific part of table: ([string]$var+'hasdf').GetType().Name

see all properties and methods: | Get-Member
