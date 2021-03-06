## Docker & RabbitMQ basics and notes

1. Setup and run Docker
2. Run multiple Web API's
3. Setup Microsoft SQL Server  
4. Setup message broker

#### Docker 
##### Commands  

Login  
docker login  
usermod -aG docker $USER (access without sudo)  

Manage  
docker build -t simpleapi (csproj name) .  
docker run -d -p 1236:80 simpleapi (run in background)  
docker ps (containers)  
docker ps -a (all)  
docker images  
docker rm (container)  
docker rmi (image)  
docker rmi $(docker images -f "dangling=true" -q)  

Publish  
docker tag docker201 iankesh/docker201  
docker push iankesh/docker201  

#### RabbitMQ  
##### Commands  
docker run -d --hostname my-rabbit --name Rabbit -e RABBITMQ_DEFAULT_USER=root -e RABBITMQ_DEFAULT_PASS=root -p 15672:15672 -p 5672:5672 rabbitmq:3-management

#### Sql Server  
connect - docker exec -it [container id] /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P [pass]
commands - https://www.sqlshack.com/working-sql-server-command-line-sqlcmd/

use VS Code SQL Server extension for db managing   
https://hub.docker.com/_/microsoft-mssql-server  
https://docs.microsoft.com/en-us/ef/core/miscellaneous/cli/dotnet  
https://www.nuget.org/packages/dotnet-ef/   

##### Cheat sheet for code first
sudo docker run -d -p 5000:80 xx  
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Aa123456' -p 1433:1433 -d mcr.microsoft.com/mssql/server:2017-latest   
dotnet ef migrations add {fix model}   
dotnet ef database update  
sudo docker run -d -p 5000:80 xx  
sudo docker build -t xx .   

#### Images
MS SQL https://hub.docker.com/_/microsoft-mssql-server  
Rabbit MQ https://hub.docker.com/_/rabbitmq/

#### References
- Setup on IIS using VSCode https://dotnetplaybook.com/deploy-a-net-core-api-with-docker/
- Docker for windows https://docs.docker.com/docker-for-windows/
- Docker commands https://docs.docker.com/engine/reference/commandline/run/
- Docker Hub https://hub.docker.com/ 
- RabbitMQ https://www.rabbitmq.com/tutorials/tutorial-one-dotnet.html  
- RabbitMQ https://registry.hub.docker.com/_/rabbitmq/  
