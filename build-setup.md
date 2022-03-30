1. Install Nerdbark Git Versioning tool (nbgv)
2. Add nuget.config file next to your sln file (requires VS restart)
3. Copy build folder to your application folder
4. Update Solution Name in the .nuke/parameters.json file
5. Create the version.json file under each component that must be versioned (required for GitVersioning to calculate the semantic version number)
6. Create deployment_list.json file (required for the pipeline to know which components should be packed for deployment)
