# Blazor Web App Container Support Validation

Sample applications used to validate container support for Blazor Web App templates as part of ASP.NET Core validation efforts. The repository includes samples for all Blazor Web App render modes with Docker/containerization scenarios for testing and verification.

## Prerequisites

Ensure the following software is installed before running the samples:

- .NET SDK: **11.0.100-preview.7.26381.103**
- Visual Studio 2026 Insiders: **[12023.133] Professional**
- Any application (such as Docker Desktop or Rancher Desktop) that provides a **Docker daemon container engine**

### Context Menu Samples

For these samples, container support was added from the project context menu after project creation.
- `ContainerSupport-ContextMenu/StaticSSR`
- `ContainerSupport-ContextMenu/InteractiveServer`
- `ContainerSupport-ContextMenu/InteractiveWebAssembly`
- `ContainerSupport-ContextMenu/InteractiveAuto`

### Creation Dialog Samples

For these samples, container support was enabled from the creation dialog during project creation.
- `ContainerSupport-On-CreationDialog/StaticSSR`
- `ContainerSupport-On-CreationDialog/InteractiveServer`
- `ContainerSupport-On-CreationDialog/InteractiveWebAssembly`
- `ContainerSupport-On-CreationDialog/InteractiveAuto`

## Running the Samples in a Container in Debug Mode from VS 2026 Insiders

### Steps

1. Open the desired sample project in **Visual Studio 2026 Insiders**.
2. Ensure that **Docker Desktop** or **Rancher Desktop** is running.
3. Select the **Container (Dockerfile)** launch profile and start the application by selecting **Run** or pressing **F5**.
4. The application will launch in a container and open in the browser.

**Note:** For the `InteractiveWebAssembly` and `InteractiveAuto` samples, ensure that the **Server** project is configured as the startup project before running the application.

## Running the Samples in a Container via the Docker CLI (Published Output Release mode)

### Steps

1. Open a terminal and navigate to the directory containing the sample's `Dockerfile`.
   - For `InteractiveWebAssembly` and `InteractiveAuto`, navigate to the **solution root directory**.
2. Ensure that **Docker Desktop** or **Rancher Desktop** is running.
3. Build the container image.

For Static SSR and Interactive Server.
   
```bash
docker build -t image-name .

Example
docker build -t interactive-server .
```

For Interactive WebAssembly and Interactive Auto samples, run the Docker build command from the solution root directory.

```bash
docker build -f ProjectName/Dockerfile -t image-name .

Example
docker build -f InteractiveWebAssembly/Dockerfile -t interactive-webassembly .
```

5. Run the container.

 ```bash
docker run -p 9005:8080 --name=container-name image-name

Example:
docker run -p 9005:8080 --name=interactive-server interactive-server
```
7. Open the containerized application in your browser: http://localhost:9005
