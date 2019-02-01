## Dependencies
  * docker
  * docker-compose
  * git
  * maven  

## Build
  `rm build/webapps/*`(PS) or `rm build/webapps/* -rf`(bash)  
  `cd jcommune/; mvn clean package; cd ..`  
  `cp jcommune/jcommune-view/jcommune-web-view/target/jcommune.war build/webapps`  
  `cd poulpe; mvn clean package; cd ..`  
  `cp poulpe/poulpe-view/poulpe-web-view/target/poulpe.war build/webapps`  

  ```
    docker-compose build
  ```

##Start
First start a DB and give it some time to start
```
docker-compose up db
```

When the DB is ready for connections start the app:
```
docker-compose up app
```
