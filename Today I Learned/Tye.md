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