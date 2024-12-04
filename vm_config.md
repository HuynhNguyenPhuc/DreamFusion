# Virtual Machine Configuration on Google Cloud


## NVIDIA Product
### NVIDIA Driver
* Install the ubuntu-drivers tool:
```
sudo apt install ubuntu-drivers-common
```
* Install the best-suited driver for your hardware:
```
sudo ubuntu-drivers autoinstall
```
* Reboot the system
```
sudo reboot
```

### Build Essential (for gcc and g++)
```
sudo apt install build-essential
```

### NVIDIA CUDA Toolkit
* Follow this installation guide: https://docs.nvidia.com/cuda/cuda-installation-guide-linux/#meta-packages
* Configure the environment variable PATH for CUDA Toolkit:
  - Open the .bashrc File
  ```
  nano ~/.bashrc
  ```
  - Add CUDA path to the end of this file
  ```
  export PATH=/usr/local/cuda/bin:$PATH
  export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
  ```
  - Save and reset the configuration
  ```
  source ~/.bashrc
  ```

### NVIDIA Container Toolkit
* Follow this installation guide: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html
* Note: Don't forget to configure Docker after installing.


## Docker
### Docker installation
* Set up the Docker's apt repository
```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
* Install the Docker packages
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
* Verify that the installation is successful by running the hello-world image
```
sudo docker run hello-world
```
### Docker post-installation
Read the instruction: https://docs.docker.com/engine/install/linux-postinstall/ to create the docker group and add your user.


## Miniconda (Additional)
* Install miniconda
```
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
```
* Refresh the system
```
source ~/miniconda3/bin/activate
```
* Initialize conda on all available shells
```
conda init --all
```