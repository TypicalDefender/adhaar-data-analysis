# aadhaar-data-analysis

![pic-explain](https://i.pinimg.com/originals/37/7c/dd/377cddb66172c99e930627f328993b0b.jpg)






Deployment Guide

Once tag is created get the tag into your local system


  > git fetch

checkout to the created tag

  > git checkout <tag>

Install the node_modules

  > yarn install

Build the project with release param

  > yarn run build --release

Zip the build folder with a name which is <projectName_version_date.zip>

  > zip -r project-name-v0.11.111-11-11-2019.zip build

copy the same zipped file to the server in which you are planning to deploy

  > scp project-name-v0.11.11-11-11-2019.zip scts@192.168.0.33:~

ssh to the server where you would like to deploy

  > ssh scts@192.168.*.*

Change the directory to acads-releases folder

  > cd project-releases

Create a new folder inside acads-releases with version name

  > mkdir v0.11.111

mv acads-settings-v0.11.111-11-11-2019.zip to this created folder

  > mv ../../project-name-v0.11.111-11-11-2019.zip .

unzip the acads-settings-v0.11.111-11-11-2019.zip file

  > unzip project-name-v0.11.111-11-11-2019.zip

change directory to Build

  > cd build

copy pm2.json, Dockerfile, deploy.sh file from the previous versions.

  > cp ../../v0.11.1/build/pm2.json .
  > cp ../../v0.11.1/build/Dockerfile .
  > cp ../../v0.11.1/build/deploy.sh .

check if a docker is already running

  > sudo docker container ps

if a docker is already running with acads project remove the Docker container

  > sudo docker container rm -f <container id>

deploy the new container

  > sudo ./deploy.sh

once the deployment is done check if the container is running or not

  > sudo docker container ps
