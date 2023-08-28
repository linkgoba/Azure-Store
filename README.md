# Azure Store

## Docker

Setup local bridge network so our Docker containers (PetStoreApp, PetStorePetService, PetStoreProductService & PetStoreOrderService can all communicate)

![image](https://github.com/linkgoba/Azure-Store/assets/129736461/f8f84fb6-c354-4060-bbf3-4d907c66ef31)

1. Have Docker build PetStorePetService Docker Image. (This is a multi stage Docker build, it  will compile the PetStorePetService code and build our Docker Image containing this Spring Boot jar and all of the dependencies.)

` docker build -t petstoreservice . `
` docker image ls `

2. Instruct Docker to  start a running container with the following petstorepetservice:latest image, forwarding port 8081 to the Spring Boot App running on 8081. The PETSTOREPETSERVICE_SERVER_PORT is one of several environment variables.

` docker run --rm --net petstorebridge --name petstorepetservice -p 8081:8081 –e PETSTOREPETSERVICE_SERVER_PORT=8081 -d petstorepetservice:latest ` 
` docker ps `

![image](https://github.com/linkgoba/Azure-Store/assets/129736461/4abf15d4-a8aa-4ebf-a2e1-242867e76fed)

3. Have Docker build PetStoreOrderService Docker Image. (This is a multi stage Docker build, it will compile the PetStoreOrderService code and build our Docker Image containing this Spring Boot jar and all of the dependencies.

` docker build -t petstorepetservice . `

4. Instruct Docker to start a running container with the following petstoreproductservice:latest image, forwarding port 8082 to the Spring Boot App running on 8082. The PETSTOREPRODUCTSERVICE_SERVER_PORT is one of several environment variables that we will introduce over the course of these guides. 

` docker run --rm --net petstorebridge --name petstoreproductservice -p 8082:8082 -e PETSTOREPRODUCTSERVICE_SERVER_PORT=8082 -d petstoreproductservice:latest `

5. Have Docker build PetStoreOrderService Docker Image. (This is a multi stage Docker build, it will compile the PetStoreOrderService code and build our Docker Image containing this Spring Boot jar and all of the dependencies.

` docker build -t petstoreorderservice . `

6. Instruct Docker to start a running container with the following petstoreorderservice:latest image, forwarding port 8083 to the Spring Boot App running on 8083. The PETSTOREORDERSERVICE_SERVER_PORT is one of several environment variables that we will introduce over the course of these guides.

` docker run --rm --net petstorebridge --name petstoreorderservice -p 8083:8083 -e  PETSTOREORDERSERVICE_SERVER_PORT=8083 -d petstoreorderservice:latest `

7. Build store app docker image

```  
cd to azure-cloud/petstore/petsotreapp
docker build -t petstoreapp
docker image ls
```


