# dockerpractice
run docker

#-------------------------------------------------
# Introduction to Docker by mirik Astahov



docker run hello-world

docker ps 
docker ps -a
docker images


docker search tomcat
docker pull tomcat
docker run -it -p 1234:8080 tomcat
docker run -it -p 8888:80 nginx
docker run -d -p 8888:80 nginx


docker build -t mirik .
docker images

docker run -it  -p 1234:80  mirik:latest
docker run -d -p  1234:80  mirik:latest

docker  ps     # list containers
docker  ps -a  # list all containers

docker tag mirik_ubuntu mirik_ubuntu-PROD
docker tag mirik_ubuntu mirik_ubuntu-PROD:v2

docker rm   # delete container
docker rmi  # delete image

UPDATE IMAGE
~~~~~~~~~~~~~
docker run -d -p 7777:80 mirik_ubuntu4
docker exec -it 5267e21d140 /bin/bash
echo "V2" >> /var/www/html/index.html
exit
docker commit 5267e21d140 mirik_v2:latest

Export/Import Docker Image to file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker save image:tag > arch_name.tar
docker load -i arch_name.tar


Import/Export Docker Image to AWS ECR
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker build -t mirik:v1 .
aws ecr get-login --no-include-email --region=ca-central-1 
docker tag  mirik:v1  12345678.dkr.ecr.ca-central-1.amazonaws.com/myrepo:latest
docker push 12345678.dkr.ecr.ca-central-1.amazonaws.com/myrepo:lastest

docker pull 12345678.dkr.ecr.ca-central-1.amazonaws.com/myrepo:latest



Kill and Delete Containers and Images
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker rm -f $(docker ps -aq)        # Delete all Containers
docker rmi -f $(docker images -q)    # Delete all Images

