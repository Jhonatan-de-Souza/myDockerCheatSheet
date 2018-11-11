# My Docker Cheat Sheet
The most used commands I find myself using everyday with docker

### Initial Setup, Check Version, also doubles as a check if docker is installed correctly
1. `sudo docker version`
2. `sudo groupadd docker`
3. `sudo usermod -aG docker $linuxusername`

### Basic download and go set up
1. `docker container run -d --name nameofcontainer -p 80:80 nameofimagetodownloadoruse`
2. `docker ps -a`
3. `docker container stop nameofcontainer`
4. `docker container rm nameofcontainer`
5. `docker image ls`

# Checking state of Containers and images
### check running images (used to create containers)
`sudo docker images`
### check running containers (An instance of an image)
`sudo docker ps`
### Detailed docker info
`sudo docker info`
### Check all running containers  
`sudo docker container ls -a`

### Whats going on in Containers
`docker container top`
`docker container inspect`
`docker container stats`

# Modifiyig state of docker containers

### Running a docker container with SQL Server Express using default config
in which case i pass the 3 mandatory parameters(called environment variables) with the -e flag  and also map the port that it will use with the -p flag also run it as a background service with the -d flag and finally and persist the data my mapping to a location in my local drive like  for example-> /LocalDirectoryPath:/var/opt/msqql 

`sudo docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=yourStrong(!)Password' -e 'MSSQL_PID=Express' -p 1433:1433 -v /home/fuktik/Documents/SQLServerData:/var/opt/mssql -d  microsoft/mssql-server-linux:latest`

`docker container run -d --name nameofcontainer -p 80:80 nginx`

## Starting and Stopping Containers
### Stoping a container (changes status to exited)
`sudo docker stop containerName`
### Removing the Containers
`sudo docket container rm `

# Getting and using downloaded images
`sudo docker pull mcr.microsoft.com/mssql/server`


## Getting inside a container with a shell(SSH Like) Inside of Containers
### start new container intereactively
`docker container run -it nameofcontainer bash`
### run additional command in existing container
`docker container exec -it nameofcontainer bash`  

## Publishing Rules
--publish is always in the format HOST:CONTAINER



# Connecting multiple dockers containers (Automatic DNS Resolution between containers)

## Network commands
 1. `docker network ls`  // Show network
 2. `docker network inspect` //Inspect a network
 3. `docker network create drivename` //  Create a network
 4. `docker network connect` // Attach a network to container
 5. `docker network disconnect ` // Detatch a network from container
  
One way to connect containers and allow network comunnication with them is that you create a them in the same "virtual network" by creating them in the same network instead of the default "bridge" driver, example:
`docker container run -d --name my_nginx --network my_app_net nginx`
1. If you don't specify the virtual network name it will default to the container's name, and then you will have to manually link the containers using the `--link` list commands
