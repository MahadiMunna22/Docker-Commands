# Docker Commands

### dockerFile
```
FROM node:17-alpine
RUN npm install -g nodemon
WORKDIR /app
COPY . .
EXPOSE 4000
CMD ["node", "run", "dev"]
```

## Image
### Build Image
```docker build -t myApp```
### List Image
```docker images```
### Delete Image
```
docker image rm myApp
docker image rm myApp -f
```
## Container
### Build Container
```
docker run —name myApp_C -p 4000:4000 -d myApp
docker run —name myApp_C -p 4000:4000 --rm -v [absolute path] -d myApp
```
### Run Existing Container
```docker start myApp_C```
### List Container
```docker ps -a```
### Delete Container
```docker container rm myApp_C myApp_C1```

### Delete Everything
```docker system prune -a```

## Docker Compose
* Create file “docker-compose.yaml”
* Write docker commands
* Run “docker-compose up” to start building and creating image & containers
* Run “docker-compose down” to stop the server

### docker-compose.yaml
```
version: “2.32.0”,
services: 
    api:
        build: ./api
        container_name: api_c
        ports:
            - '4000:4000'
        volumes:
            - ./api:/app
            - /app/node_modules
```
