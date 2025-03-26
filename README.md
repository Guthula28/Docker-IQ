# Docker-IQ

# 1. What is Docker ? 
Docker is an open Source platform for developing,shipping and running applications in lightweight containers.it ensures consistency across
environments
use case : Developers can package an application and its dependencies into a container to run reliably in different environments

# 2. Explain the difference between image and containers ?
   image : Docker image in read only template contains set of instructions to create a container.
   
   Container : it is a running instance of docker image 

# 3. How to you create a Docker image ? 
   Use a Docker file to define the build process and docker build to create the image
   Example : 
       FROM ubuntu:latest
       RUN apt-get update && apt-get install -y curl
       CMD ["echo",Hello Docker"]
     docker build -t image 

# 4. What is the difference between docker run and docker start ?
   Docker run creates and starts a new container
   Docker start an existing stopped container. it doesn,t create a new container

# 5. How do you check running docker containers ?
    use docker ps for running containers and ps -a for all containers including stopped containers 

# 6. What is the purpose of docker-compose ?
   it simplifies multi-container application deployment using a YAML file
   example: 
        Version: "3"
         services :
            web:        
               image: nginx
               ports:
                  -"8080:80"

# 7. How to delete unused docker images ?
   use docker image prune -a
   EX: docker image prune -f

# 8. what is the difference between COPY AND ADD in docker file ?
   Both copy files to the image,but ADD supports additional features like extracting archieves 
   Exa: COPY source /app/source
        ADD archieve.tag.gz /app/archieve

# 9. How do you expose a port in docker container ?
   use the EXPOSE keyword in the docker file or -p in the docker run command
   Exa: EXPOSE 80
     Docker run -p 8080:80 nginx

# 10. How do you log into a running Docker container ? 
    docker exec -it <container  eid> /bin/bash

# 11. Explain docker volumes and their types ?
    Docker volumes store data outside the container lifecycle. 
      Types :
            Named Volumes : Managed by docker
            Bind mounts : Host file system paths
      Example : docker volume create myvolume
                docker run -v myvolume:/app/data nginx

# 12. what is the purpose of docker network ?
   Docker networking is a feature that enables communication between containers.its essential for connecting containers each 
      other outside world. Types include
      Bridge
      Host
      none and overlay
      exa : docker network create mynetwork
            docker run --network mynetwork nginx   

# 13. How do you build multi-stage Dockerfile ?
    Multi-stage builds optimize image size by using Multiple FROM statements 
      FROM golang:alpine as builder
      RUN go build -o app main.go
      FROM alpine
      COPY --from=builder /app/app
      CMD ["/app']

# 14. How do you limit container resources ?
    use flags like --memory and --cpus
      EXAM :    DOCKER RUN --memory=500m --cpus=1 nginx

# 15. How do you troubleshoot a failing container ?
    check logs : docker logs <containerid>
    inspect : docker inspect <container id>

# 16. What is docker hub and how do you push image to it ? 
     Docker hub is a Cloudbased registry service provided by docker allows users to find,store and share the container images
      docker push username/myimage

# 17. How do you run container in detached mode ?
    use the -d flag
    exam : docker run -d nginx1

# 18. What is the difference between ENTRYPOINT AND CMD 
   "ENTRYPOINT is used to define a mandatory command that always executes when the container starts, while CMD provides a 
    default command that can be easily overridden when running the container. ENTRYPOINT is best for fixed behavior, whereas 
    CMD is for default behavior that can be changed."















   
