### Generate a Personal Access Token
Make sure that your generate a Personal Access Token in your VSTS account. This token will be used to authorize the process to restore Nuget packages [Follow this document](https://docs.microsoft.com/en-us/vsts/accounts/use-personal-access-tokens-to-authenticate?view=vsts).

### Create a NuGet.Config
Place the config file in same folder with `*.csproj`  
Replace following content:  
1. source name
2. source url. Example: https://zhqqitest.pkgs.visualstudio.com/_packaging/zhiqing-feed/nuget/v2
3. Username. You can input anystring in this value.
4. ClearTextPassword. Input the PAT generated in last step.
```
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <activePackageSource>
    <add key="nuget.org" value="https://www.nuget.org/api/v2/" />
  </activePackageSource>
  <packageSources>
    <add key="{REPLACE_WITH_SOURCE_NAME}" value="{REPLACE_WITH_SOURCE_URL}" />
  </packageSources>
  <packageSourceCredentials>
    <zhiqing-feed>
        <add key="Username" value="{REPLACE_WITH_ANY_STRING}" />
        <add key="ClearTextPassword" value="{REPLACE_WITH_PAT}" />
    </zhiqing-feed>
</packageSourceCredentials>
</configuration>
```

### Modify Dockerfile
Add a command to copy NuGet.Config between `COPY *.csproj ./` and `RUN dotnet restore`

```
COPY *.csproj ./
COPY NuGet.Config* ./
RUN dotnet restore
```