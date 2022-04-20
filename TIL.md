https://gist.github.com/leandromonaco

# Angular

## Install Angular CLI Tool

the latest NodeJS LTS is required

1. Run ```npm install -g @angular/cli```
2. Run ```ng --version```

## Create a new Angular App

1. Run ```ng new NewApp.UI --strict false```
2. Would you like to add Angular routing? ```Yes```
3. Which stylesheet format would you like to use? ```CSS```
4. Navigate to the NewApp.UI folder
5. Run ```ng serve``` (Angular Development Server)

# Docker

## Build and Run container

1. Navigate to the folder where the Dockerfile is stored
2. Run ```docker build -t angular-container:1.0 .```
3. Search ImageID by running ```docker images```
4. Run ```docker run -p 80:80 469b3a773ed7```

## Dockerfile example
```
FROM node:lts as node

RUN npm install -g @angular/cli

WORKDIR /usr/src/app
COPY src/TeamHub.UI/ ./my-app/

WORKDIR /usr/src/app/my-app
RUN npm install
RUN npm run build

FROM nginx:alpine
COPY --from=node /usr/src/app/my-app/dist/team-hub.ui /usr/share/nginx/html
```

# Entity Framework

## Install/Update
1. Install EF command ```dotnet tool install -g dotnet-ef --version 3.0.0```
2. Update EF command (if required) ```dotnet tool update -g dotnet-ef --version 6.0.3```

## Create/Update Model (Database First)
1. csproj file must reference  ```Microsoft.EntityFrameworkCore.Design``` and ```Microsoft.EntityFrameworkCore.SqlServer``` nuget packages
2. Navigate to the folder where you want to store the model
3. Update EF Model Classes ```dotnet ef dbcontext scaffold "Server=localhost;Database=DbName;Trusted_Connection=True;" Microsoft.EntityFrameworkCore.SqlServer -o Database -f```
    
# GitHub

## Reset author for ALL commits
```
git filter-branch -f --env-filter "GIT_AUTHOR_NAME='Newname'; GIT_AUTHOR_EMAIL='new@email'; GIT_COMMITTER_NAME='Newname'; GIT_COMMITTER_EMAIL='new@email';" HEAD
git push --force --tags origin 'refs/heads/main'
```

## Read Git Configuration
```
git config -l
```

## Removing sensitive data from a repository
- https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository
- https://rtyley.github.io/bfg-repo-cleaner/

## Troubleshoot git issues

```
set GIT_TRACE=1
set GIT_CURL_VERBOSE=1
```

## Fix .gitignore issues

1. Run ```git rm -r --cached .``` to unstage and remove the path to your files from the Git index.
2. Execute ```git add .``` to re-add all your files back (only the correct files will be updated).
3. Execute ```git commit -m ".gitignore is now working"``` to commit all your files back into the Git index.


# NodeJS

## Installation with [Node Version Manager](https://github.com/coreybutler/nvm-windows)

```
nvm install latest
nvm install lts
nvm install 12.18.4
nvm list
nvm use 12.18.4
nvm current
```

# Tye

## Reference Material
- [ReadMe](https://github.com/dotnet/tye/blob/main/docs/README.md)
- [Schema](https://github.com/dotnet/tye/blob/main/docs/reference/schema.md)
- [Getting Started](https://github.com/dotnet/tye/blob/main/docs/getting_started.md)

## Installation

```
dotnet tool uninstall -g Microsoft.Tye
dotnet tool install -g Microsoft.Tye --version "0.11.0-alpha.22111.1"
tye --version
```

## Execute

1. Execute ```tye run --dashboard --debug```

## Configuration

```yaml
name: mysite

services:

- name: My-Website
  project: ../src/Website/Website.csproj
  bindings:
  - name: website
    port: 52091
    host: website.local

- name:  My-API
  project: ../src/API/API.csproj
  bindings:
  - name: api
    port: 52090
    host: localhost/swagger/index.html
    
- name: sql-database
  image: mcr.microsoft.com/mssql/server:2019-latest
  bindings:
  - connectionString: Data Source=host.docker.internal,1433;Initial Catalog=sqldatabase;Persist Security Info=True;User ID=sa;Password=${env:SA_PASSWORD}
    port: 1433
  env:
  - name: SA_PASSWORD
    value: 4dm1nP4ssw0rd
  - name: ACCEPT_EULA
    value: Y

- name: redis
  image: redis
  bindings:
  - port: 6379
    connectionString: "${host}:${port}"

- name: redis-cli
  image: redis
  args: "redis-cli -h redis MONITOR"
```

# Windows Subsystem for Linux (WSL)

Some features, such as the ability to run graphical Linux applications, are only available on Windows 11.

## Install Ubuntu

 * Documentation: https://help.ubuntu.com
 * Management: https://landscape.canonical.com
 * Support: https://ubuntu.com/advantage

1. Open Powershell window with admin rights
2. Run ```wsl --install -d Ubuntu```
3. Create a [default UNIX user account](https://docs.microsoft.com/en-us/windows/wsl/setup/environment#set-up-your-linux-username-and-password)

## Create Self-Signed SSL Certificate

1. Open a command prompt window
2. Run ```ubuntu```
3. Copy and Paste the following code. This will generate a .crt and a .key using [OpenSSL](https://www.openssl.org/)
``` 
PARENT="localhost"
openssl req \
-x509 \
-newkey rsa:4096 \
-sha256 \
-days 18250 \
-nodes \
-keyout $PARENT.key \
-out $PARENT.crt \
-subj "/CN=${PARENT}" \
-extensions v3_ca \
-extensions v3_req \
-config <( \
  echo '[req]'; \
  echo 'default_bits= 4096'; \
  echo 'distinguished_name=req'; \
  echo 'x509_extension = v3_ca'; \
  echo 'req_extensions = v3_req'; \
  echo '[v3_req]'; \
  echo 'basicConstraints = CA:FALSE'; \
  echo 'keyUsage = nonRepudiation, digitalSignature, keyEncipherment'; \
  echo 'subjectAltName = @alt_names'; \
  echo '[ alt_names ]'; \
  echo "DNS.1 = ${PARENT}"; \
  echo '[ v3_ca ]'; \
  echo 'subjectKeyIdentifier=hash'; \
  echo 'authorityKeyIdentifier=keyid:always,issuer'; \
  echo 'basicConstraints = critical, CA:TRUE, pathlen:0'; \
  echo 'keyUsage = critical, cRLSign, keyCertSign'; \
  echo 'extendedKeyUsage = serverAuth, clientAuth')

openssl x509 -noout -text -in $PARENT.crt
```
3. Run ```openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt``` to get a .pfx
4. Run ```explorer.exe .``` to open Windows Explorer and get the Certificate files

**Notes**

- CRT file does not contain the private key
- KEY file contains the private key
- PFX file contains the private key, but it's protected by a password (eg. 12345)

## Import Self-Signed SSL Certificate

Reference
- [Import-PfxCertificate](https://docs.microsoft.com/en-us/powershell/module/pki/import-pfxcertificate?view=windowsserver2022-ps)
- [Trusted Root Certification Authorities Certificate Store](https://docs.microsoft.com/en-us/windows-hardware/drivers/install/trusted-root-certification-authorities-certificate-store)

1. Open a PowerShell window with admin rights 
2. Run ```Get-Credential -UserName 'Enter password below' -Message 'Enter password below'```
3. Run ```Import-PfxCertificate -FilePath "C:\GitHub\Workbench\Misc\SSL\localhost.pfx" -CertStoreLocation Cert:\LocalMachine\Root\ -Password $mypwd.Password```

# WinGet

Install [winget](https://winget.run) and search packages

```
winget install Microsoft.VisualStudioCode --override '/SILENT /mergetasks="!runcode,addcontextmenufiles,addcontextmenufolders"'
winget install -e --id Postman.Postman
winget install -e --id Microsoft.VisualStudioCode
winget install -e --id Microsoft.VisualStudio.2019.Professional
winget install -e --id Microsoft.VisualStudio.2022.Enterprise
winget install -e --id Docker.DockerDesktop
winget install -e --id Datalust.Seq
winget install -e --id Microsoft.Edge.Dev
winget install -e --id Microsoft.Edge
winget install -e --id Microsoft.SQLServer.2019.Express
winget install -e --id Microsoft.SQLServerManagementStudio
winget install -e --id Microsoft.DeploymentToolkit
winget install -e --id Microsoft.dotnet
winget install -e --id Microsoft.dotnetHostingBundle
winget install -e --id Microsoft.dotnetRuntime.6-x64
winget install -e --id Microsoft.dotnetRuntime.5-x64
winget install -e --id Microsoft.dotNetFramework
winget install -e --id Microsoft.webpicmd
winget install -e --id Microsoft.PowerToys
winget install -e --id Microsoft.WindowsTerminal
winget install -e --id Microsoft.GitCredentialManagerCore
winget install -e --id Microsoft.PowerShell
winget install -e --id Microsoft.PowerShell.Preview
winget install --id Microsoft.Git
winget install --id Microsoft.VFSforGit
winget install -e --id Microsoft.XMLNotepad
winget install -e --id Notepad++.Notepad++
winget install -e --id 7zip.7zip
winget install -e --id Microsoft.WingetCreate
winget install -e --id ekvedaras.redis-gui
```
