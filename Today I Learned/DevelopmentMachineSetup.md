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

# 6 - Install Visual Studio
```
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
```
DISM /online /enable-feature /featurename:IIS-ManagementConsole
DISM /online /enable-feature /featurename:IIS-NetFxExtensibility45
DISM /online /enable-feature /featurename:IIS-ASPNET45
DISM /online /enable-feature /featurename:IIS-ISAPIExtensions
DISM /online /enable-feature /featurename:IIS-ISAPIFilter
DISM /online /enable-feature /featurename:IIS-DefaultDocument
DISM /online /enable-feature /featurename:IIS-DirectoryBrowsing
DISM /online /enable-feature /featurename:IIS-HttpErrors
DISM /online /enable-feature /featurename:IIS-StaticContent
DISM /online /enable-feature /featurename:IIS-HttpLogging
DISM /online /enable-feature /featurename:IIS-HttpCompressionStatic
DISM /online /enable-feature /featurename:IIS-Security
```
## Reference Material

- [DISM - Deployment Image Servicing and Management](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/dism---deployment-image-servicing-and-management-technical-reference-for-windows)
- DISM /online /get-features /format:table
- DISM /online /get-featureinfo /featurename:[feature name]
- DISM /online /disable-feature /featurename:[feature name]
- DISM /online /enable-feature /featurename:[feature name]

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
winget install -e --id Microsoft.dotnet
winget install -e --id Microsoft.dotnetHostingBundle
winget install -e --id Microsoft.dotnetRuntime.6-x64
winget install -e --id Microsoft.dotnetRuntime.5-x64
winget install -e --id Microsoft.dotNetFramework
winget install -e --id Microsoft.webpicmd
winget install -e --id ekvedaras.redis-gui
winget install -e --id Microsoft.PowerShell
winget install -e --id Microsoft.PowerShell.Preview
winget install -e --id Microsoft.PowerAutomateDesktop
winget install -e --id Gauge.Gauge
```

# Development Utilities
```
winget install -e --id ScooterSoftware.BeyondCompare4
winget install -e --id LINQPad.LINQPad.7
winget install -e --id Microsoft.XMLNotepad
winget install -e --id Notepad++.Notepad++
winget install -e --id WinMerge.WinMerge
winget install -e --name Sysinternals
winget install -e --id Microsoft.WindowsTerminal
```

# Misc
```
winget install -e --id 7zip.7zip
winget install -e --id Microsoft.PowerToys
winget install -e --id VideoLAN.VLC
winget install -e --id ShareX.ShareX
winget install -e --id Grammarly.ForOffice
winget install -e --id Grammarly.ForWindows
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
