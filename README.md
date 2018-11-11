# myDockerCheatSheet
The most used commands I find myself using everyday with docker

### Initial Setup, Check Version, also doubles as a check if docker is installed correctly
1. `sudo docker version`
2. `sudo groupadd docker`
3. `sudo usermod -aG docker $fuktik`

### Basic download and go set up
1. `docker container run -d --name nameofcontainer -p 80:80 nameofimagetodownloadoruse`
2. `docker ps -a`
3. `docker container stop nameofcontainer`
4. `docker container rm nameofcontainer`
5. `docker image ls`

# Checking state of Containers and images
### check running containers (Can have use many images)
`sudo docker ps`
### check running images (Can be contained in many containers)
`sudo docker images`
### Detailed docker info
`sudo docker info`
### Check all running containers
`sudo docker container ls -a`

# Modifiyig state of docker containers

### Running a docker container with SQL Server Express using default config
in which case i pass the 3 mandatory parameters(called environment variables) with the -e flag  and also map the port that it will use with the -p flag also run it as a background service with the -d flag and finally and persist the data my mapping to a location in my local drive like  for example-> /LocalDirectoryPath:/var/opt/msqql 

`sudo docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=yourStrong(!)Password' -e 'MSSQL_PID=Express' -p 1433:1433 -v /home/fuktik/Documents/SQLServerData:/var/opt/mssql -d  microsoft/mssql-server-linux:latest`

`docker container run -d --name nameofcontainer -p 80:80 nginx`

## Stop and Starting Containers
### Stoping a container (changes status to exited)
`sudo docker stop containerName`
### Removing the Containers
`sudo docket container rm `


# Getting and using downloaded images
`sudo docker pull mcr.microsoft.com/mssql/server`