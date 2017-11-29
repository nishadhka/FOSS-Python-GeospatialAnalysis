# Basic workshop requirement

1. Hardware with 64 bit OS, windows 10 and Mac latest updated version to run docker software, workshop is heavily dependent on docker and please ensure it is working in your computer, test docker by downloading and running the images helloworld and ubuntu
1. Google earth desktop version software
1. Quantum GIS software
1. Latest workshop Github repo folder in local- https://github.com/nishadhka/FOSS-Python-GeospatialAnalysis/archive/master.zip

# The workshop image set up with docker

1. Download the workshop image tar file from google drive with [this](https://drive.google.com/file/d/1qvrpxsz9YHWNtZHNxkYGQ4syz0JdwxY4/edit) link, do visit this workshop page to get the latest/updated version of the docker image. The tar file is 4.6 GB in size, please cheksum the downloaded tar to ensure its hash as 57e05b908790697e07f553d684bf5607
1. Uuse docker as follows, to load the tar into docker as an image
```   
docker load -i foss_pt_gsa_ubuntu_v1.tar
```
1. To check the docker is loaded with images, ensure the image foss-pt-gsa/foss-pt-gsa:version1 is listed
```
docker images
```
1. To run the image
```
docker run -dit foss-pt-gsa/foss-pt-gsa:version1
```
1. Get the CONTAINER_ID from the command ```docker ps```
1. To enter into the image bash
```
docker exec -it CONTAINER_ID bash
```
1. After enter into the image’s bash terminal, enter following commands. the commands download the workshop github repo zip file into a working direcoty, then unzip it and get into the repo folder to start a jupter notebook server
```
cd /home/ubuntu/
wget https://github.com/nishadhka/FOSS-Python-GeospatialAnalysis/archive/master.zip
unzip master.zip
cd FOSS-Python-GeospatialAnalysis-master
jupyter notebook --ip 0.0.0.0 --no-browser --allow-root
```
1. Note down the link provided by the jupyter notebook such as example http://0.0.0.0:8889/?token=c8e944b8397b0bde97b4d9284e5e3ffc0136658fcca3ea1e
1. Logout from the docker image bash(by typing ctrl+q or closing the bash window) and in the host computer note down the image_ID of the workshop image running inside the docker by
```
docker ps
```
1. Then inspect about the docker image to get to know the image’s IP address. Note down the ipaddress
```
docker inspect image_ID
```
1. Edit the jupter server given link as into http://ipaddress:8889/?token=c8e944b8397b0bde97b4d9284e5e3ffc0136658fcca3ea1e
1. Open the link in host computer browser, it shows the Jupyternotebooks in the workshop repo and click on the file docker_test.ipynb, to run the notebook and excute its first cell to ensure all the libraries for the workshop is working properly
1. Open other jupyter notebooks inside the folders for workshop flow
1. The files created in the docker can be tranfered to host computer to view the files in QGIS, enter command ```docker ps``` in your host computer, note down the ```NAMES```, enjoy interesting names provided by docker itself, use following command\
```
docker cp optimistic_jang:/home/ubuntu/FOSS-Python-GeospatialAnalysis-master /home/yourhost/location/
```
