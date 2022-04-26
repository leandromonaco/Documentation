# WinGet

1. Install from https://aka.ms/getwinget
2. Check installation with ```winget --version```

![WindowsTerminal_KmYQFR6mEb](https://user-images.githubusercontent.com/5598150/165411040-9037b37d-9c4b-4d2d-b93b-799a6e57e860.gif)

## Reference Material
- https://aka.ms/winget-command-help
- https://docs.microsoft.com/en-us/windows/package-manager/winget/install
- [The Windows Package Manager Manifest Creator command-line tool ](https://github.com/microsoft/winget-create)

# Install WSL with Ubuntu
- Documentation: https://help.ubuntu.com
- Management: https://landscape.canonical.com
- Support: https://ubuntu.com/advantage

1. Open Powershell window with admin rights
2. Run wsl --install -d Ubuntu
3. Create a default UNIX user account

# NodeJS Installation with Node Version Manager

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

# IDE / Build Tools
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

# Browsers
```
winget install -e --id Microsoft.Edge.Dev
winget install -e --id BraveSoftware.BraveBrowser
winget install -e --id Microsoft.Edge
winget install -e --id Google.Chrome.Dev
winget install -e --id Mozilla.Firefox.DeveloperEdition
winget install -e --id Opera.Opera
```

# Git
```
winget install -e --id GitHub.GitHubDesktop
winget install -e --id GitHub.cli
winget install -e --id GitHub.GitLFS
winget install -e --id Microsoft.Git
winget install -e --id Microsoft.VFSforGit
winget install -e --id Microsoft.GitCredentialManagerCore
winget install -e --id Atlassian.Sourcetree
```

# Dev Tools
```
winget install -e --id Postman.Postman
winget install -e --id Docker.DockerDesktop
winget install -e --id Datalust.Seq
winget install -e --id Microsoft.SQLServer.2019.Express
winget install -e --id Microsoft.SQLServerManagementStudio
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

# Utilities
```
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
