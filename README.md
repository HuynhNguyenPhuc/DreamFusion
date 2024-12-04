# NVIDIA Nemo

## Install via Docker
```
docker pull nvcr.io/nvidia/nemo:24.09
```

## Start a container
* We can start a container directly by running the following command:
```
docker run --gpus all --ipc=host --ulimit memlock=-1 --ulimit stack=67108864 -d nvcr.io/nvidia/nemo:24.09
```
* 

## Access the bash in the container
```
docker exec -it nvcr.io/nvidia/nemo:24.09 /bin/bash
```