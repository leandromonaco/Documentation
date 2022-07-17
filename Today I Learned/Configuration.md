# Code
```csharp
private static ConfigurationManager GetConfiguration(ConfigurationManager configurationManager)
        {
            configurationManager
                         .SetBasePath(Environment.CurrentDirectory)
                         .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
                         .AddJsonFile($"appsettings.Development.json", optional: true, reloadOnChange: true)
                         .AddEnvironmentVariables("Lambda:")
                         .Build();

            return configurationManager;
        }
```

# Mapping and Override

The : separator doesn't work with environment variable hierarchical keys on all platforms. __, the double underscore, is supported by all platforms. 

From <https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-6.0#non-prefixed-environment-variables>


# Set Environment Variable

- ```setx Lambda__ModuleConfiguration__Infrastructure__Cognito__ValidIssuer   "SOME VALUE" /M```
- ```setx Lambda__ModuleConfiguration__Infrastructure__Cognito__ClientId  "SOME VALUE" /M```
 
# Troubleshooting
https://stackoverflow.com/questions/53870781/asp-net-core-addenvironmentvariables-doesnt-load-variables
