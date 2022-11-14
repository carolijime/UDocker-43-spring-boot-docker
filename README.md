#Spring Boot and Docker

Source code in this repo is to support my on line course for Docker and Spring Boot. 

You can learn more about my course [here](http://courses.springframework.guru).

## Note: ALWAYS install in this order:
1) Maven Clean Package
2) Docker Build

#Command (in terminal window) to create JAR file of the project (without docker image)
mvn clean package

#Command (in terminal window) to create JAR file of the project (with docker image) - make sure Docker is open and no processes are running
mvn clean package docker:build

1) Create repo in docker hub (online)
2) Create settings.xml file:
   1) right click on <Configuration> tag (in pom file) > Maven > Create 'settings.xml'
3) Make sure that username and password in settings file and <docker.image.prefix> (in pom) have your docker username there
4) Make sure that <docker.image.name> (in pom) have the created repository's name

#Command (in terminal window) to create JAR file of the project (with docker image) and push to docker hub
- make sure Docker is open and no processes are running
- add (code at the end of this file) docker credentials to settings.xml file
mvn clean package docker:build docker:push

#Command (in terminal window) to create JAR file of the project (with docker image) and push to docker hub
passing docker credentials
- make sure Docker is open and no processes are running
mvn clean package docker:build -D'docker.username'=carolijime -D'docker.password'=HxCqV5bWNo37U9 docker:push

#How to do a new release (skip if docker template is in place, should be in place)
1) Change release name/number in pom file
2) Change release name/number in Dockerfile (hardcoded there), use same name as pom file 

#Below are some useful commands
#To check if we are able to log into docker hub
docker login 

#To "manually" push
docker push [username/reponame]

#run maven docker (container)
mvn docker:run  (run no on background)
mvn docker:start (run on background)

#stop maven docker(container)
mvn docker:stop

#How to add (IF DESIRED) docker credetials in settings.xml file
<servers>
<server>
<id>docker.io</id>
<username>[username]</username>
<password>[password]</password>
</server>
</servers>