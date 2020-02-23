# azure-kubernetes-tutorial

A simple tutorial on setting up, creating a container and deploying to a kubernetes cluster on Azure

This tutorial shows how to run an ASP.NET Core app in a Docker container. Then deploy the container to Azure Container Registry and an Azure Kubernetes Cluster.

In this tutorial, you:
> * Create ASP.NET Core web API
> * Run the api locally
> * Build & run the api in Docker Linux containers


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
