# Project Tye

- [Documentation](https://github.com/dotnet/tye/blob/main/docs/README.md)
- [Getting Started](https://github.com/dotnet/tye/blob/main/docs/getting_started.md)
- [Recipes](https://github.com/dotnet/tye/tree/main/docs/recipes)
- [Samples](https://github.com/dotnet/tye/tree/main/samples)

1. Go to the solution folder
2. Run ```tye init``` to generate ```tye.yaml```
3. Run ```tye run --dashboard``` (where the ```tye.yaml``` file is located)

## Tye.yaml

```
extensions:
- name: elastic
  logPath: ./.logs

name: servicetemplate
services:
- name: servicename-api
  project: ServiceName.API/ServiceName.API.csproj

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

- name: redis
  image: redis
  bindings:
  - port: 6379
    connectionString: "${host}:${port}"

- name: redis-cli
  image: redis
  args: "redis-cli -h redis MONITOR"

ingress:
- name: ingress
  bindings:
    - port: 8080
  rules:
    - path: /A
      service: servicename-api
```

