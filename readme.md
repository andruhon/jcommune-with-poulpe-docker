#Jcommune and Poulpe in Docker
This project refers to https://github.com/jtalks-org/jcommune and https://github.com/jtalks-org/poulpe/ as submodules please do clone with:
```git clone --recurse-submodules git@github.com:andruhon/jcommune-with-poulpe-docker.git```

## Dependencies
  * docker
  * docker-compose
  * git
  * maven  
  * JDK

## Build
  `rm build/webapps/*`(PS) or `rm build/webapps/* -rf`(bash)  
  `cd jcommune/; mvn clean package; cd ..`  
  `cp jcommune/jcommune-view/jcommune-web-view/target/jcommune.war build/webapps/`  
  `cd poulpe; mvn clean package; cd ..`  
  `cp poulpe/poulpe-view/poulpe-web-view/target/poulpe.war build/webapps/`  

  ```
    docker-compose build
  ```

## Start
First start a DB and give it some time to start:
```
docker-compose up db
```

When the DB is ready for connections in another console start the app:
```
docker-compose up app
```

Wait for a message similar to this one
```
app_1  | Feb 01, 2019 4:01:03 AM org.apache.coyote.AbstractProtocol start
app_1  | INFO: Starting ProtocolHandler ["http-apr-8080"]
app_1  | Feb 01, 2019 4:01:03 AM org.apache.coyote.AbstractProtocol start
app_1  | INFO: Starting ProtocolHandler ["ajp-apr-8009"]
app_1  | Feb 01, 2019 4:01:03 AM org.apache.catalina.startup.Catalina start
app_1  | INFO: Server startup in 44421 ms
```

Now the app should be available at http://localhost:8888/jcommune/  
The admin panel should be available at http://localhost:8888/poulpe/  

## Debugging
If the application does not work, open another console and try to connect to the app container:  
List all containers:  
```
docker container ls --all
``` 
The container name is usually `jcommune-with-poulpe-docker_app_1`  
Connect to the container using the name from the command above:  
```
docker exec -it jcommune-with-poulpe-docker_app_1 /bin/bash
```
View the log and look for errors:
```
less logs/jcommune.log
```