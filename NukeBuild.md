https://nuke.build/docs/common/cli-tools/
https://nuke.build/


1. Install [nbgv .NET Core CLI tool](https://github.com/dotnet/Nerdbank.GitVersioning/blob/master/doc/nbgv-cli.md)
2. Add [nuget.config](https://github.com/leandromonaco/Documentation/blob/main/nuget.config) file next to your sln file (requires VS restart)
3. Create build folder under your application and copy the files from [PipelineTemplate](https://github.com/leandromonaco/Documentation/tree/main/PipelineTemplate)
4. Update Solution Name in the [.nuke/parameters.json](https://github.com/leandromonaco/Documentation/blob/5f67d5628d3217874dd82a3c6a6351e42f2adb69/PipelineTemplate/nuke/parameters.json#L3) file
5. Create the [version.json](https://github.com/leandromonaco/Documentation/blob/main/version.json) file under each component that must be versioned (required for GitVersioning to calculate the semantic version number)
6. Create deployment_list.json file (required for the pipeline to know which components should be packed for deployment)
