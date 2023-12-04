# Use the official .NET SDK image as a base image
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

# Set the working directory in the container
WORKDIR /app

# Copy the project file to the working directory
COPY *.csproj .

# Restore NuGet packages
RUN dotnet restore

# Copy the remaining source code to the working directory
COPY . .

# Build the application
RUN dotnet publish -c Release -o out

# Use the official ASP.NET runtime image as a base image
FROM mcr.microsoft.com/dotnet/aspnet:6.0

# Set the working directory in the container
WORKDIR /app

# Copy the published output from the build image to the runtime image
COPY --from=build /app/out .

# Specify the entry point for the container
ENTRYPOINT ["dotnet", "YourAppName.dll"]
