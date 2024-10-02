# Chocolatey offline installer
Whenever I'd not not use configuration management and offline installation tasks there, I go back to this notes. <br> Got me packet with all self hosted dependencies pwsh, .Net Framework 4.8.1 and 7zip. <br>
It's based on official documentation: https://docs.chocolatey.org/en-us/choco/setup/#chocolatey-cli-v20


1. Prerequisites are present on [Windows machine](https://docs.chocolatey.org/en-us/chocolatey-components-dependencies-and-support-lifecycle/#supported-windows-versions):
   - [PowerShell 3.0+](https://docs.chocolatey.org/en-us/chocolatey-components-dependencies-and-support-lifecycle/#supported-powershell-versions)
   - [.NET Framework 4.8+](https://docs.chocolatey.org/en-us/choco/setup/#chocolatey-cli-v20)
   - 7zip or you can enable windows built in option in _install.ps1_ file
     - `set $env:chocolateyUseWindowsCompression = 'true'`
  
2. Downloaded install.ps1 script from https://community.chocolatey.org/install.ps1 and locate into your preferred directory, for this example I used <br>
 `C:\OfflineInstaller`
3. Download Chocolatey package you intend to install, locate it to same directory as _install.ps1_ in previous step.
4. In _install.ps1_ file I edited value for `$ChocolateyDownloadUrl =`. Do check the script and adjust it to your liking❕
```
[CmdletBinding(DefaultParameterSetName = 'Default')]
param(
    # The URL to download Chocolatey from. This defaults to the value of
    # $env:chocolateyDownloadUrl, if it is set, and otherwise falls back to the
    # official Chocolatey community repository to download the Chocolatey package.
    # Can be used for offline installation by providing a path to a Chocolatey.nupkg.
    [Parameter(Mandatory = $false)]
    [string]
    $ChocolateyDownloadUrl = 'file:C:\OfflineInstaller\chocolatey.2.3.0.nupkg',
```
5. Open up PowerShell and run `install.ps1`

----
This project includes content derived from the official Chocolatey documentation. Portions of this documentation are modifications based on work created and shared by the Chocolatey community. <br>
Official [Chocolatey Documentation](https://docs.chocolatey.org/) :: Official License [Apache License 2.0](https://github.com/chocolatey/docs?tab=Apache-2.0-1-ov-file#readme) <br>
