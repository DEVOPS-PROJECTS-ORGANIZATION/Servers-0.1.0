# Servers

Application that list servers. Data are fixed and application does not use database as a storage.

Dockerfile contains two runtime stages: 
- **appServerRuntime**  - Spring Boot application server that provides REST API.
- **appWebServerRuntime** - Spring Boot application that provides REST API and contains Angular front-end [web application](https://github.com/DanijelRadakovic/Servers-Front)

[BuildKit](https://github.com/moby/buildkit) is used for building container images.

In order to build **appServerRuntime** image run the following command (Dockerfile has to be in current working directory):

```shell
DOCKER_BUILDKIT=1 docker build --target appServerRuntime -t danijelradakovic/servers:0.1.0 .
```

In order to build **appServerRuntime** image run the following command (Dockerfile has to be in current working directory):
```shell
DOCKER_BUILDKIT=1 docker build --target appServerRuntime -t danijelradakovic/servers:0.1.0-web .
```

## appServerRuntime Instructions (Spring Boot REST API)
If you're using Docker for Windows, Then simply start the desktop app installed in:
```
C:\Program Files\Docker\Docker\Docker Desktop.exe
```
Start Docker Daemon with Windows PowerShell
```
start "C:\Program Files\Docker\Docker\Docker Desktop.exe"
```
After you right clicking Docker’s whale icon in task bar. You’ll see ‘Quit Docker Desktop’ item in list.
```
Task bar → Docker’s whale icon → right click → Quit Docker Desktop
```
## appWebServerRuntime Instructions (Spring Boot REST API + Angular front-end)
