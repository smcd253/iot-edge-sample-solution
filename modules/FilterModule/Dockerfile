FROM microsoft/dotnet:2.0-sdk AS build-env
WORKDIR /app

COPY *.csproj ./
COPY NuGet.Config* ./
ENV NUGET_API_KEY $NUGET_API_KEY
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o out

FROM microsoft/dotnet:2.0-runtime
WORKDIR /app
COPY --from=build-env /app/out ./
ENTRYPOINT ["dotnet", "FilterModule.dll"]