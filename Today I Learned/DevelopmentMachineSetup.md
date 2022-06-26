# 1 - Install WinGet

1. Install from https://aka.ms/getwinget
2. Check installation with ```winget --version```

![WindowsTerminal_KmYQFR6mEb](https://user-images.githubusercontent.com/5598150/165411040-9037b37d-9c4b-4d2d-b93b-799a6e57e860.gif)

## Reference Material
```winget install --help```
- https://aka.ms/winget-command-help
- https://docs.microsoft.com/en-us/windows/package-manager/winget/install
- [The Windows Package Manager Manifest Creator command-line tool ](https://github.com/microsoft/winget-create)

# 2 - Install WSL with Ubuntu
- Documentation: https://help.ubuntu.com
- Management: https://landscape.canonical.com
- Support: https://ubuntu.com/advantage

1. Open Powershell window with admin rights
2. Run wsl --install -d Ubuntu
3. Create a default UNIX user account

# 3 - Install GIT
```
winget install -e --id Git.Git
winget install -e --id GitHub.GitHubDesktop
winget install -e --id GitHub.cli
winget install -e --id GitHub.GitLFS
winget install -e --id Microsoft.Git
winget install -e --id Microsoft.VFSforGit
winget install -e --id Microsoft.GitCredentialManagerCore
winget install -e --id Atlassian.Sourcetree
winget install -e --id TortoiseGit.TortoiseGit
```

# 4 - Install NodeJS

1. https://github.com/coreybutler/nvm-windows/releases
2. Click on nvm-setup.zip
3. Extract and install it (Reboot might be required)
4. Type the below command to verify if your nvm installation was successful. $ nvm --version

```
nvm install latest
nvm install lts
nvm install 12.18.4
nvm list
nvm use 12.18.4
nvm current
```

# 5 - Install Angular CLI Tool

the latest NodeJS LTS is required

1. Run ```npm install -g @angular/cli```
2. Run ```ng --version```

# 6 - Install Visual Studio & .NET Frameworks

Search .NET Versions ```winget search --id Microsoft.dotnet```

```
winget install -e --id Microsoft.dotnet -v 6.1.21.52711
winget install -e --id Microsoft.dotnet
winget install -e --id Microsoft.dotnetHostingBundle
winget install -e --id Microsoft.DotNet.Runtime.3_1
winget install -e --id Microsoft.DotNet.AspNetCore.3_1
winget install -e --id Microsoft.DotNet.Runtime.5
winget install -e --id Microsoft.DotNet.AspNetCore.5
winget install -e --id Microsoft.DotNet.Runtime.6
winget install -e --id Microsoft.DotNet.AspNetCore.6
winget install -e --id Microsoft.dotNetFramework
winget install -e --id Microsoft.VisualStudioCode
winget install -e --id Microsoft.VisualStudio.2019.Professional
winget install -e --id Microsoft.VisualStudio.2022.Enterprise
winget install -e --id Microsoft.VisualStudio.2022.TestController
winget install -e --id Microsoft.VisualStudio.2022.TestAgent
winget install -e --id Microsoft.VisualStudio.2022.TeamExplorer
winget install -e --id Microsoft.VisualStudio.2022.Professional
winget install -e --id Microsoft.VisualStudio.2022.Enterprise
winget install -e --id Microsoft.VisualStudio.2022.Community
winget install -e --id Microsoft.VisualStudio.2022.BuildTools
```

## Reference Material

- [Import or export installation configurations](https://docs.microsoft.com/en-us/visualstudio/install/import-export-installation-configurations)

# 7 - Install SQL Server
```
winget install -e --id Microsoft.SQLServer.2019.Express
winget install -e --id Microsoft.SQLServer.2019.Developer --override '/QUIET /IACCEPTSQLSERVERLICENSETERMS /CONFIGURATIONFILE="C:\Dev\SQLConfigurationFile.ini"'
winget install -e --id Microsoft.SQLServerManagementStudio
```

## SQLConfigurationFile.ini
```
; Microsoft SQL Server Configuration file  
[OPTIONS]  
; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE.  
; This is a required parameter.  
ACTION="Install"  
; Specifies features to install, uninstall, or upgrade.  
; The list of top-level features include SQL, AS, RS, IS, and Tools.  
; The SQL feature will install the database engine, replication, and full-text.  
; The Tools feature will install Management Tools, Books online,   
; SQL Server Data Tools, and other shared components.  
FEATURES=SQL,Tools
INSTANCENAME=SQL2019Dev
SQLSYSADMINACCOUNTS="[Domain]\[Username]"
SECURITYMODE=SQL
SAPWD="M3rz0ug4!!!!"
```

## Reference Material
- [Install SQL Server from the Command Prompt](https://docs.microsoft.com/en-us/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt)
- [Install SQL Server using a configuration file](https://docs.microsoft.com/en-us/sql/database-engine/install-windows/install-sql-server-using-a-configuration-file)

# 8 - Enable Windows Features (Windows 10)

List all features: ```DISM /online /get-features /Format:Table```

```
DISM /online /enable-feature /featurename:IIS-WebServerRole
DISM /online /enable-feature /featurename:IIS-WebServerManagementTools
DISM /online /enable-feature /featurename:IIS-ManagementConsole
DISM /online /enable-feature /featurename:IIS-NetFxExtensibility45
DISM /online /enable-feature /featurename:IIS-ISAPIExtensions
DISM /online /enable-feature /featurename:IIS-ISAPIFilter
DISM /online /enable-feature /featurename:IIS-ASPNET45
DISM /online /enable-feature /featurename:IIS-DefaultDocument
DISM /online /enable-feature /featurename:IIS-DirectoryBrowsing
DISM /online /enable-feature /featurename:IIS-HttpErrors
DISM /online /enable-feature /featurename:IIS-StaticContent
DISM /online /enable-feature /featurename:IIS-HttpLogging
DISM /online /enable-feature /featurename:IIS-HttpCompressionStatic
DISM /online /enable-feature /featurename:IIS-Security
DISM /online /enable-feature /featurename:IIS-IPSecurity
DISM /online /enable-feature /featurename:IIS-BasicAuthentication
DISM /online /enable-feature /featurename:IIS-WindowsAuthentication                 
DISM /online /enable-feature /featurename:IIS-DigestAuthentication      
DISM /online /enable-feature /featurename:IIS-URLAuthorization            
DISM /online /enable-feature /featurename:IIS-ClientCertificateMappingAuthentication
DISM /online /enable-feature /featurename:IIS-IISCertificateMappingAuthentication   
DISM /online /enable-feature /featurename:IIS-CertProvider
```
## Reference Material

- [DISM - Deployment Image Servicing and Management](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/dism---deployment-image-servicing-and-management-technical-reference-for-windows)
- DISM /online /get-features /format:table
- DISM /online /get-featureinfo /featurename:[feature name]
- DISM /online /disable-feature /featurename:[feature name]
- DISM /online /enable-feature /featurename:[feature name]

# 9 - Install Certificates

1. Run ```Import-Certificate -FilePath "C:\Dev\SSL\MyLocalCertificateAuthority.crt" -CertStoreLocation Cert:\LocalMachine\Root\```
2. Run ```$mypwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force```
3. Run ```Import-PfxCertificate -FilePath "C:\Dev\SSL\mydomain.com.pfx" -CertStoreLocation Cert:\LocalMachine\My\ -Password $mypwd.Password```

Optional

```$mypwd = Get-Credential -UserName 'Enter password below' -Message 'Enter password below'```

# 10 - Install VSCode Extensions
```
code --install-extension amazonwebservices.aws-toolkit-vscode
code --install-extension angular.ng-template
code --install-extension johnpapa.angular-essentials
code --install-extension johnpapa.angular2
code --install-extension kendoui.kendotemplatewizard
code --install-extension dbaeumer.vscode-eslint
code --install-extension ms-vscode.vscode-typescript-next
code --install-extension ms-vscode.powershell
code --install-extension ms-dotnettools.csharp
code --install-extension ms-azuretools.vscode-docker
code --install-extension ms-kubernetes-tools.vscode-kubernetes-tools
code --install-extension ms-vsliveshare.vsliveshare
code --install-extension esbenp.prettier-vscode
code --install-extension ms-edgedevtools.vscode-edge-devtools	
code --install-extension GitHub.codespaces
code --install-extension GitHub.remotehub
code --install-extension GitHub.vscode-codeql
code --install-extension GitHub.classroom
code --install-extension Atlassian.atlascode
code --install-extension ms-playwright.playwright
code --install-extension vsblox.blox
code --install-extension bierner.markdown-mermaid
code --install-extension pflannery.vscode-versionlens
code --install-extension wix.vscode-import-cost
code --install-extension eamodio.gitlens
code --install-extension pranaygp.vscode-css-peek
code --install-extension usernamehw.errorlens
code --install-extension ms-azuretools.vscode-tye
code --install-extension SonarSource.sonarlint-vscode
```

# 10 - Install Visual Studio 2022 Extensions
```powershell

#Credits: https://gist.github.com/ScottHutchinson/b22339c3d3688da5c9b477281e258400
#$PackageName = "AmazonWebServices.AWSToolkitforVisualStudio2022"
#$PackageName = "GitHub.copilotvs"
#$PackageName = "SteveCadwallader.CodeMaid"
#$PackageName = "SteveCadwallader.CodeMaidVS2022"
#$PackageName = "ironcev.sharpen"
#$PackageName = "SonarSource.SonarLintforVisualStudio2022"
$PackageName = "DevExpress.CodeRushforVS2022"

$ErrorActionPreference = "Stop"
 
$baseProtocol = "https:"
$baseHostName = "marketplace.visualstudio.com"
 
$Uri = "$($baseProtocol)//$($baseHostName)/items?itemName=$($PackageName)"
$VsixLocation = "$($env:Temp)\$([guid]::NewGuid()).vsix"
 
$VSInstallDir = "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\ServiceHub\Services\Microsoft.VisualStudio.Setup.Service"
 
if (-Not $VSInstallDir) {
  Write-Error "Visual Studio InstallDir registry key missing"
  Exit 1
}
 
Write-Host "Grabbing VSIX extension at $($Uri)"
$HTML = Invoke-WebRequest -Uri $Uri -UseBasicParsing -SessionVariable session
 
Write-Host "Attempting to download $($PackageName)..."
$anchor = $HTML.Links |
Where-Object { $_.class -eq 'install-button-container' } |
Select-Object -ExpandProperty href

if (-Not $anchor) {
  Write-Error "Could not find download anchor tag on the Visual Studio Extensions page"
  Exit 1
}
Write-Host "Anchor is $($anchor)"
$href = "$($baseProtocol)//$($baseHostName)$($anchor)"
Write-Host "Href is $($href)"
Invoke-WebRequest $href -OutFile $VsixLocation -WebSession $session
 
if (-Not (Test-Path $VsixLocation)) {
  Write-Error "Downloaded VSIX file could not be located"
  Exit 1
}
Write-Host "VSInstallDir is $($VSInstallDir)"
Write-Host "VsixLocation is $($VsixLocation)"
Write-Host "Installing $($PackageName)..."
Start-Process -Filepath "$($VSInstallDir)\VSIXInstaller" -ArgumentList "/q /a $($VsixLocation)" -Wait
 
Write-Host "Cleanup..."
rm $VsixLocation
 
Write-Host "Installation of $($PackageName) complete!"
```

# Create IIS Websites

Powershell 7+ is required

1. Run ```Install-Module -Name IISAdministration -Scope AllUsers -AllowClobber```
2. Run ```New-IISSite -Name 'website_name' -PhysicalPath 'C:\Inetpub\wwwroot' -BindingInformation "*:443:hostname1.com" -Protocol https -SslFlag "Sni" -CertificateThumbPrint "[Insert Thumbprint]" -CertStoreLocation "Cert:\LocalMachine\My" -Force```
3. Run ```New-IISSiteBinding -Name "website_name" -BindingInformation "*:443:hostname2.com" -Protocol https -SslFlag "Sni" -CertificateThumbPrint "[Insert Thumbprint]" -CertStoreLocation "Cert:\LocalMachine\My" -Force```

# Change host file

```powershell

$HostFile = 'C:\Windows\System32\drivers\etc\hosts'
 
# Create a backup copy of the Hosts file
$dateFormat = (Get-Date).ToString('dd-MM-yyyy hh-mm-ss')
$FileCopy = $HostFile + '.' + $dateFormat  + '.copy'
Copy-Item $HostFile -Destination $FileCopy
 
$Bindings = Get-IISSiteBinding "websitename.com"

# Get the contents of the Hosts file
$File = Get-Content $HostFile
 
# write the Entries to hosts file, if it doesn't exist.
foreach ($Binding in $Bindings) 
{
    $HostFileEntry = $Binding.bindingInformation
    $HostFileEntry = $HostFileEntry -replace "\*:443:", ""
    
    Write-Host "Checking existing HOST file entries for $HostFileEntry..."
     
    #Set a Flag
    $EntryExists = $false
     
    if ($File -contains "127.0.0.1 `t $HostFileEntry") 
    {
        Write-Host "Host File Entry for $HostFileEntry already exists."
        $EntryExists = $true
    }
    #Add Entry to Host File
    if (!$EntryExists) 
    {
        Write-host "Adding Host File Entry for $HostFileEntry"
        Add-content -path $HostFile -value "127.0.0.1 `t $HostFileEntry"
    }
}

```
# Configure IP/Port Mapping
![image](https://user-images.githubusercontent.com/5598150/173493508-1a874845-8bb7-49ea-9c67-f7e217e923dc.png)


# Browsers
```
winget install -e --id Microsoft.Edge.Dev
winget install -e --id BraveSoftware.BraveBrowser
winget install -e --id Microsoft.Edge
winget install -e --id Google.Chrome.Dev
winget install -e --id Mozilla.Firefox.DeveloperEdition
winget install -e --id Opera.Opera
```

# Dev Tools
```
winget install -e --id Postman.Postman
winget install -e --id Docker.DockerDesktop
winget install -e --id Datalust.Seq
winget install -e --id Microsoft.DeploymentToolkit
winget install -e --id Microsoft.webpicmd
winget install -e --id qishibo.AnotherRedisDesktopManager
winget install -e --id Microsoft.PowerShell
winget install -e --id Microsoft.PowerShell.Preview
winget install -e --id Microsoft.PowerAutomateDesktop
winget install -e --id Gauge.Gauge
```

# Development Utilities
```
dotnet tool install -g Microsoft.Tye --version "0.11.0-alpha.22111.1"
winget install -e --id ScooterSoftware.BeyondCompare4
winget install -e --id LINQPad.LINQPad.7
winget install -e --id Microsoft.XMLNotepad
winget install -e --id Notepad++.Notepad++
winget install -e --id WinMerge.WinMerge
winget install -e --name Sysinternals
winget install -e --id Microsoft.WindowsTerminal
winget install -e --id Telerik.Fiddler.Everywhere
winget install -e --id WiresharkFoundation.Wireshark
winget install -e --id=Amazon.NoSQLWorkbench 
winget install DevToys
```

# Misc
```
winget install "Files App"
winget install -e --id 7zip.7zip
winget install -e --id Microsoft.PowerToys
winget install -e --id VideoLAN.VLC
winget install -e --id ShareX.ShareX
winget install -e --id Grammarly.ForOffice
winget install -e --id Grammarly.ForWindows
winget install -e --id OBSProject.OBSStudio
winget install -e --id JGraph.Draw
winget install -e --id GIMP.GIMP
```

# AWS
```
winget install -e --id Amazon.AWSCLI
winget install -e --id Amazon.SAM-CLI
```

# Azure
```
winget install -e --id Microsoft.AzureCLI
```

# Others

[Custom Prompt Setup](https://docs.microsoft.com/en-us/windows/terminal/tutorials/custom-prompt-setup)
