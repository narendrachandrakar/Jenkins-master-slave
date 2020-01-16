
Docker Installation:
https://docs.docker.com/install/linux/docker-ce/debian/


Docker Build and Docker Run for the Jenkins Container:

docker build -t jenkins-master .
docker build -t jenkins-slave .

docker-compose -f docker-compose.ci.yml up

docker-compose -f docker-compose.ci.yml down
