# docker-roboshop-best-practice
Updating the docker roboshop with best practice


# Best Practices for Dockerfile
1. Use official minimal base images. Alpine images are minimal and lightweight.
2. Use multi docker layer implementation, build image at one stage and get the results to other stage
3. Don't run any container with root access. Create user for any container
4. Always EXPOSE Port
5. Always better to create WORKDIR for our code
6. Avoid using latest -> we will not be sure which version actually running
7. Use volumes if containers are stateful, prefer stateless apps inside containers not stateful
8. Use ENV variables at runtime instead of build time.. no need to rebuild the image
9. Use ENTRYPOINT + CMD Correctly
10. Version and Tag Images Properly prefer semantic version
11. Use secrets, dont hardcodes creds


## Commands
```shell

To build and run all the containers
docker compose up -d 

To build specific containers without cache
docker compose build catalogue cart --no-cache

To run specific container
docker compose run catalogue

To create network 
docker network create roboshop

To disconnect any service from bridge network
docker network disconnect bridge frontend

To connect any service to roboshop network
docker network connect roboshop frontend

To build image
docker build -t catalogue:1.2.0 .

To run image
docker run -d --name catalogue --network roboshop catalogue:1.2.0
```