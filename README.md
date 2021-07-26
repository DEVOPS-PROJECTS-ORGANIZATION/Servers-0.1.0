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
**Start Docker Daemon:** If you're using Docker for Windows, Then simply start the desktop app installed in:
```
C:\Program Files\Docker\Docker\Docker Desktop.exe
```
Position yourself in the folder where dockerfile is
```
cd DOCKERFILE_PATH
```
Create Docker image from Dockerfile with Docker BuildKit (**Generating .jar binary file**; .jar file is not already generated, so we need to map source code to .jar file)
```
docker image build --target DOCKERFILE_STAGE -t DOCKER_HUB_USERNAME/IMAGE_NAME:VERSION DOCKERFILE_PATH
```
```
docker image build --target appServerRuntime -t danijelradakovic/servers:0.1.0 .
```
Creates and runs Docker containers (Interactive mode; Container port forwarding)
```
docker run -MODE --name CONTAINER_NAME -p HOST_PORT:CONTAINER_PORT IMAGE_NAME
```
```
docker run -MODE --name CONTAINER_NAME -p PUBLISHED_PORT:EXPOSED_PORT IMAGE_NAME
```
```
docker run -it --name servers-0.1.0 -p 9000:8080 danijelradakovic/servers:0.1.0
```
Request:
```GET http://localhost:9000/api/server```  
```
http://localhost:9000/api/server
```
Response:
```json
[
{"id":0,"hostname":"database","domain":"db.aws.com","os":"LINUX"},
{"id":1,"hostname":"sftp","domain":"sftp.aws.com","os":"LINUX"},
{"id":2,"hostname":"datalake","domain":"s3.aws.com","os":"LINUX"}
]
```
**Stop Docker Daemon:** After you right clicking Docker’s whale icon in task bar. You’ll see ‘Quit Docker Desktop’ item in list.
```
Task bar → Docker’s whale icon → right click → Quit Docker Desktop
```
## appWebServerRuntime Instructions (Spring Boot REST API + Angular front-end)
