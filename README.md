## Free and Open Source libraries of Python for Geo spatial Analysis and Visualisation(Maps and Satellite imageries)

Geospatial representation are so prevalent in day to day life, such as even in simple travel related conversation to maps, aerial/satellite images etc. In digital era, geospatial data is extensively produced and consumed in ever growing proportion. Python with its free and open source libraries are giving wide variety yet simple and effective set of tools to visualise and analyse geospatial data. The current workshop is directed for beginners of Python programming language, who have basic understanding on computing and data formats. The primary objective of the workshop is to introduce and give hands on training on selected list of FOSS libraries for geospatial analysis. The workshop as a do it yourself fashion tries to solve two real world problems in Geographical Information System (GIS) and its geospatial data sources.

The workshop comprised of three components: 

**Component 1: Introduction**

Python environment and work flow setup, an assisted task of setting up the Docker and Jupyter notebook setup. Setting up the Geographical Information System (GIS) environment with extended discussion. Setting up of GIS tools such as FOSS QGIS and Google earth. This component is comprised of four exercises. 1. Introduction to vector data, 2. Introduction to raster data, 3. binary and text file formats of geospatial data, 4. Introduction to tools of GIS, 5. Introduction to literal programming- Jupyter notebook

**Component 2: work with vector data**

Find characteristics of road network(type of road network, length of the type) within a 1X1 km grid. The data source is Open Street Map (OSM) road network data on a city level (60X60km size). This operation is operationally simple such as measure a line feature but computationally intensive as the operation comprised of geometry within operation on dense road network seen in urban setup. Libraries such as Shapely, Fiona, Geopandas and rtree index will be used for the fast processing of this operation. This component comprised of three exercises 1. Find distance between two points 2. Find distance between two points constrained by another vector 3. Find distance between large number of points in for loop

**Component 3: work with raster data**

Find cloud cover percentage over area of interest. The data source is Landsat satellite imagery. Searching cloud free Landsat images over an Area of Interest for a temporal extent of a year or more is manual and time consuming. Applying cloud cover detection algorithm could make this operation automatic. Libraries such as rasterio, Geopandas, Fiona, and libraries related to landsat algorithms will be used for this task. This component comprised of two exercises 1. Convert the imagery in geotiff into numpy arrays 2. Apply the algorithms to find the cloud cover

**Note :**
There won't be any environment setup session separately, participants are requested to ensure below prerequisites are working properly. 

**Workshop Plan**

2. Component 1- 40 minutes
1. Break- 5 minutes
3. Component 2- 50 minutes
1. Break- 5 minutes
4. Component 3- 50 minutes

### Workshop Prerequisites

1. Laptop 32bit/64 bit
1. Workshop material is tested on 64 bit computer, it is said to be working in 32 bit, lets experiment!
1. A copy of Docker container image from [here](https://drive.google.com/file/d/1RbnQAiRJY40xO6ty2TPXxM5-4vqG1cl_), file from the link foss-pt-gsa_v3.tar.gz is 2.5 GB in size, will be using this container for DIY

**Linux**

1. Install docker, I followed [digital ocean install tutorial ](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04),  which worked!.
1. Use docker to load downloaded tar into it as an container image, before that unzip the foss-pt-gsa_v3.tar.gz into foss-pt-gsa_v3.tar
```   
docker load -i  foss-pt-gsa_v3.tar 
```
1. To check the docker is loaded with new image, ensure the image ```foss-pt-gsa/foss-pt-gsa:version3``` is listed by entering
```
docker images
```
1. To run the image, enter
```
docker run -dit foss-pt-gsa/foss-pt-gsa:version3
```
1. Get the CONTAINER_ID of the just started container by the command ```docker ps```
1. To enter into the image bash
```
docker exec -it CONTAINER_ID bash
```
1. After enter into the image’s bash terminal, enter following commands. the commands download the workshop github repo zip file into a working direcoty, then unzip it and get into the repo folder to start a jupter notebook server 

        cd /home/ubuntu/  
        wget https://github.com/nishadhka/FOSS-Python-GeospatialAnalysis/archive/master.zip
        unzip master.zip
        cd FOSS-Python-GeospatialAnalysis-master
        jupyter notebook --ip 0.0.0.0 --no-browser --allow-root
      
1. Note down the link provided by the jupyter notebook such as example http://0.0.0.0:8889/?token=c8e944b8397b0bde97b4d9284e5e3ffc0136658fcca3ea1e
1. Logout from the docker image bash (by typing ctrl+q or closing the bash window) and in the host computer note down the image_ID of the workshop image running inside the docker by
```
docker ps
```
1. Then inspect about the docker image to get to know the image’s IP address. Note down the ipaddress
```
docker inspect image_ID | grep "IPAddress"
```
1. Edit the jupter server given link as into http://ipaddress:8889/?token=c8e944b8397b0bde97b4d9284e5e3ffc0136658fcca3ea1e
1. Open the link in host computer browser, it shows the Jupyternotebooks in the workshop repo and click on the file docker_test.ipynb, to run the notebook and execute its first cell to ensure all the libraries for the workshop is working properly

**Windows**

1. Local copy of Docker toolbox from [here](https://docs.docker.com/toolbox/toolbox_install_windows/) for windows 64 bit, for 32 bit Windows, follow this [link](https://medium.com/@chrispatten/installing-and-running-docker-on-32-bit-windows-d18b95ee1fc3).
1. Local copy boot2docker.iso from [here](http://boot2docker.io/), it is better to follow old method of docker toolbox instead of docker native software for Windows.
1. save the iso file in C:\Users\User\.docker\machine\cache\boot2docker.iso
2. Open the program Docker quick start, It will make a separate virtual machine to run the docker container
3. Under the Docker quick start program, after the virtual machine run, check docker is working by entering command ```docker ps```
4. Now, import the workshop container by
	```
	docker load -i foss-pt-gsa_v3.tar
	```
5. Then run the imported container image by 
	```
	docker run --name jupyter1 --rm -it --user root -d -p 8080:8080 jupyter/r-notebook:version3
	```
6. again check the command ```docker ps```, it would show the container is running by having a container ID
7. To get into the running docker
	```
	docker exec -it container_ID bash
	```
1. After enter into the image’s bash terminal, enter following commands. the commands download the workshop github repo zip file into a working direcoty, then unzip it and get into the repo folder to start a jupter notebook server 

        cd /home/ubuntu/  
        wget https://github.com/nishadhka/FOSS-Python-GeospatialAnalysis/archive/master.zip
        unzip master.zip
        cd FOSS-Python-GeospatialAnalysis-master
        jupyter notebook --ip 0.0.0.0 --no-browser --allow-root
      
1. Note down the link provided by the jupyter notebook such as example http://0.0.0.0:8080/?token=c8e944b8397b0bde97b4d9284e5e3ffc0136658fcca3ea1e
1. Logout from the docker image bash (by typing ctrl+q or closing the bash window) and in the host computer note down the image_ID of the workshop image running inside the docker by
```
docker ps
```
1. Then inspect about the docker image to get to know the image’s IP address. Note down the ipaddress
```
docker inspect image_ID | grep "IPAddress"
```
1. Edit the jupter server given link as into http://ipaddress:8889/?token=c8e944b8397b0bde97b4d9284e5e3ffc0136658fcca3ea1e
1. Open the link in host computer browser, it shows the Jupyternotebooks in the workshop repo and click on the file docker_test.ipynb, to run the notebook and execute its first cell to ensure all the libraries for the workshop is working properly
