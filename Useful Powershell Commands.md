*Useful Powershell Commands*

*Note: all commands written or found from various locations which I found useful*

**Show wifi**

```
netsh wlan show profiles
```

**show passwords**

```
name="NetworkName" key=clear
```

**Show IPaddress details**

```
Get-NetIPAddress -AddressFamily IPV4
```

**Turn ipv4 address into a variable**

```
$env:HostIP = (
    Get-NetIPConfiguration |
    Where-Object {
        $_.IPv4DefaultGateway -ne $null -and
        $_.NetAdapter.Status -ne "Disconnected"
    }
).IPv4Address.IPAddress
```

**Downloading files with Invoke-Rest**
```
$source = 'http://speedtest.tele2.net/10MB.zip'
$destination = 'c:\dload\10MB.zip'
Invoke-RestMethod -Uri $source -OutFile $destination
```
**Downloading files with BitsTransfer**
```
$source = 'http://speedtest.tele2.net/100MB.zip'
$destination = 'c:\dload\100MB.zip'
Start-BitsTransfer -Source $source -Destination $destination
```

**Execution permissions**
```
'Get-ExecutionPolicy <policy name>
    *Restricted - Scripts won't run
    *RemoteSigned - Local scripts will run, but downloaded will not unless digitally signed
    *AllSigned - Scripts will ONLY run if digitally trusted publisher
    *Unrestricted - Scripts will always run
```

## User profiles ##

*Creating a new Profile*
```
if (!(Test-Path -Path $PROFILE)) { New-Item -ItemType File -Path $PROFILE -Force }
```
*Edit existing Profile*
```
Notepad $Profile
```

*Create a service report into HTML*
```
Get-Service | ConvertTo-HTML -Property Name, Status > C:\services.htm
```
*Export to CVS*
```
Get-Service | Export-CSV c:\service.csv
```
*Export to CVS with a specific properties*
```
Get-Service | Select-Object Name, Status | Export-CSV c:\service.csv
```
*Get Event logs*
```
Get-EventLog -Log "Application"
```
*Stop Process*
```
Stop-Process -Name notepad<br> Stop-Process -ID 2668
```

*How to mass rename file extensions  inside a single directory*

```
 `Dir *.rar | Rename-Item -NewName { [io.path]::ChangeExtension($_.name, ".cbr") }`
```
> ​	Example is all of directories .rar files converted to .cbr
