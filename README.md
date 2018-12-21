# dockerusing
# Docker Hub
![alt text](https://github.com/shahin198/dockerusing/blob/master/Screenshot%20from%202018-12-21%2012-06-26.png)

# install docker
```
sudo apt-get update
sudo apt upgrade
sudo reboot
sudo apt install docker.io
```
# uninstall docker
```
sudo apt-get remove docker docker-engine docker.io
```

https://hub.docker.com

https://www.youtube.com/watch?v=lcQfQRDAMpQ&index=2&list=PL9ooVrP1hQOHUKuqGuiWLQoJ-LD25KxI5

https://www.linux.com/learn/intro-to-linux/2017/11/how-install-and-use-docker-linux

https://hub.docker.com/r/nvidia/cuda/

docker pull nvidia/digits

docker images
docker --version

https://www.youtube.com/watch?v=JprTjTViaEA

remove image frome docker

https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes

Docker Compose

https://docs.docker.com/compose/django/

```
docker pull shelmangroup/coreos-nvidia-driver-installer
sudo docker pull nvidia/cuda:8.0-runtime-ubuntu14.04
sudo docker pull nvidia/digits
sudo docker pull tensorflow/tensorflow
sudo docker images
sudo docker run <image-id>
sudo docker pull nvcr.io/nvidia/digits:18.11-caffe
sudo nvidia-docker run --name nvidia -d -p 8888:5000 nvcr.io/nvidia/digits:18.11-caffe
sudo nvidia-docker run --runtime=nvidia --rm -d -p 8888:5000 nvcr.io/nvidia/digits:18.11-caffe
# Run DIGITS on host port 5000
docker run --runtime=nvidia --name digits -d -p 5000:5000 nvidia/digits

```
# Nvidia-docker installation
https://github.com/NVIDIA/nvidia-docker

# Quickstart

Make sure you have installed the NVIDIA driver and a supported version of Docker for your distribution (see prerequisites).

If you have a custom /etc/docker/daemon.json, the nvidia-docker2 package might override it.
Ubuntu 14.04/16.04/18.04, Debian Jessie/Stretch

# If you have nvidia-docker 1.0 installed: we need to remove it and all existing GPU containers
```
docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
sudo apt-get purge -y nvidia-docker
```

# Add the package repositories
```
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update

# Install nvidia-docker2 and reload the Docker daemon configuration
sudo apt-get install -y nvidia-docker2
sudo pkill -SIGHUP dockerd

# Test nvidia-smi with the latest official CUDA image
docker run --runtime=nvidia --rm nvidia/cuda:9.0-base nvidia-smi
```
