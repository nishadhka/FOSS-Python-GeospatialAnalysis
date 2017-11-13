# The workshop
A hands on workshop on python based FOSS tools for geospatial analysis 

# Environment setup

Past experience is that it is better to have a linux environment to avoid issues in running geospatial libraries. Docker container could be a good way forward in this regard. The following points are to make a container with all libraries for FOSS-Python-GeospatialAnalysis workshop. The container is based on Jupyterhub/jupyterhub docker image which is based on debian 8 and have conda by default. The users of Windows and Mac are requested to see this [announcement](https://blog.docker.com/2016/07/docker-for-mac-and-windows-production-ready/) and follow the respective tools. As the libraries installation cost above couple of GB's in bandwidth it is requested to setup the environment before the workshop
1. To setup jupyterhub container in the docker and get into its bash terminal
    ```
    docker run -d --name jupyterhub jupyterhub/jupyterhub jupyterhub
    docker images
    docker exec -it jupyterhub bash
    ```
1. To instll required libraries
    ```
    conda config --add channels conda-forge
    dpkg --add-architecture i386 
    apt-get update
    apt-get install libsm6 libxrender1 libfontconfig1
    apt install libgl1-mesa-swx11
    conda install -c conda-forge geopandas
    conda install -c conda-forge gdal
    conda install -c conda-forge/label/broken gdal 
    ```
1. To run the jupyter notebook within the container and view it in the native OS browser
