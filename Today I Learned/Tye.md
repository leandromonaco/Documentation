## Reference Material
- [Documentation](https://github.com/dotnet/tye/blob/main/docs/README.md)
- [Schema](https://github.com/dotnet/tye/blob/main/docs/reference/schema.md)
- [Getting Started](https://github.com/dotnet/tye/blob/main/docs/getting_started.md)
- [Recipes](https://github.com/dotnet/tye/tree/main/docs/recipes)
- [Samples](https://github.com/dotnet/tye/tree/main/samples)

## Installation

```
dotnet tool uninstall -g Microsoft.Tye
dotnet tool install -g Microsoft.Tye --version "0.11.0-alpha.22111.1"
tye --version
```

## Create ```tye.yaml```

1. Go to the solution folder
2. Run ```tye init``` to generate ```tye.yaml```
3. Run ```tye run --dashboard``` (where the ```tye.yaml``` file is located)

## ```tye.yaml``` Example

```yaml

# tye application configuration file
# read all about it at https://github.com/dotnet/tye
#
# when you've given us a try, we'd love to know what you think:
#    https://aka.ms/AA7q20u
#

extensions:
- name: seq
  logPath: ./.logs

name: servicetemplate
services:

- name: nginx-ingress-controller
  image: nginx
  bindings:
    - protocol: http
      port: 51000
  volumes:
    - source: nginx.conf
      target: /etc/nginx/conf.d/default.conf
- name: servicename-api
  project: ServiceName.API/ServiceName.API.csproj
  bindings:
  - port: 51001
  replicas: 2

- name: SQL-Database
  image: mcr.microsoft.com/mssql/server:2019-latest
  bindings:
  - connectionString: Data Source=host.docker.internal,1433;Initial Catalog=ServiceDB;Persist Security Info=True;User ID=sa;Password=${env:SA_PASSWORD}
    port: 1433
  env:
  - name: SA_PASSWORD
    value: M3rz0ug4!!!!
  - name: ACCEPT_EULA
    value: Y

- name: redis-cache
  image: redis
  bindings:
  - port: 6379
    connectionString: "${host}:${port}"
  args: "redis-cli -h redis MONITOR"

```

## Execute

1. Execute ```tye run --dashboard --debug```
