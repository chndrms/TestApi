FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app


COPY *.csproj .

RUN dotnet restore 

COPY ../

RUN dotnet publish --no-restore -c Relase -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --form-build-env /app/out .
ENTRYPOINT ["dotnet","Api.dll"]