# Multi-stage build
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app

# Copy only the project file and restore dependencies
COPY *.csproj .
RUN dotnet restore

# Copy the rest of the application
COPY . .

# Build the application
FROM base AS build
WORKDIR /app
RUN dotnet publish --no-restore -c Release -o out

# Final stage for running the application --
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "Api.dll"]
