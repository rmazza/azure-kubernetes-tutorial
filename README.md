# WORK IN PROGRESS !!
# azure-kubernetes-tutorial

A simple tutorial on setting up, creating a container and deploying to a kubernetes cluster on Azure

This tutorial shows how to run an ASP.NET Core app in a Docker container. Then deploy the container to Azure Container Registry and an Azure Kubernetes Cluster.

Prerequisites:
> * [.NET Core CLI](https://docs.microsoft.com/en-us/dotnet/core/install/sdk?pivots=os-windows)
> * [Docker Desktop](https://www.docker.com/products/docker-desktop)
> * [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)

In this tutorial, you:
> * Create ASP.NET Core web API
> * Run the api locally
> * Build & run the api in Docker Linux containers

- Check the .NET Core CLI version
  ```
  dotnet --version
  ```
- Create ASP.NET Core Web API
  ```
  dotnet new webapi -n SampleAPI -o .\sample-api
  ```
- Change directory into the project
  ```
  cd .\sample-api
  ```
- Run the sample-api
  ```
  dotnet run
  ```
- Create Dockerfile
  ```
  New-Item Dockerfile
  ```
- Dockerfile
  ```
  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 as build-env
  
  ENV dockerPath /app

  WORKDIR ${dockerPath}

  COPY *.csproj ./
  RUN dotnet restore

  COPY . ./
  RUN dotnet publish -c Release -o out

  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1

  WORKDIR /app 
  COPY --from=build-env /app/out .
  ENTRYPOINT ["dotnet", "TutorialAPI.dll"]
  ```
