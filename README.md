# NVIDIA Nemo

## NVIDIA Nemo Docker Image
### Install via Docker
```
docker pull nvcr.io/nvidia/nemo:24.09
```

### Start a container
* We can start a container directly by running the following command:
```
docker run --gpus all --ipc=host --ulimit memlock=-1 --ulimit stack=67108864 -d nvcr.io/nvidia/nemo:24.09
```
* However, I have configured this process in the file *docker-compose.yml*, you should compose this file to start a container:
```
docker compose up -d
```

### Access the bash in the container
```
docker exec -it nemo  /bin/bash
```

## Some issues
* If you get errors with *opencv*, then uninstall it and try the older version:
```
pip uninstall opencv-python
pip install opencv-python==4.8.0.74
```
