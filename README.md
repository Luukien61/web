## Group-web
# Prerequisite
### Docker installation:

We recommend using Ubuntu since Docker doesn't not support directly for Windows.
It need a WSL (Windows Sub-system for Linux) to be able to run Docker.

- Windows [here](https://docs.docker.com/desktop/install/windows-install/)
- Ubuntu 
```bash
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
#To install the latest version, run:
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
- ```

After installing, check docker version:
```bash
docker -v 
docker compose version
```

# Build and run project

## Preparation
### Download docker-compose.yml file
### Ubuntu

- Navigate to foler containing docker-compose.yml file.

- Open terminal: **Ctrl+Alt+T** 

- Switch to the root user to be able to run docker commands.

    ```bash
    sudo -i
    cd /$FIlE/PATH
    ```
    Replace /$FILE/PATH with your actual file path.

    An alternative is adding the current user to docker group.
    ```bash
    sudo groupadd docker
    usermod -aG docker $USER
    ```
    Replace the $USER with the actual user name.
    
    Reboot to apply changes.

### Windows
- First, launch the Docker Desktop application.
- Navigate to the folder containing the docker-compose.yml file.
- Open CMD or Terminal



## Run

Run the below command to run project:

```bash
docker compose up -d
```
It will take a few minutes to pull images.

After that, a message like this will be showed:
```
 ✔ Container postgres-data   Started
 ✔ Container mail-server     Started       
 ✔ Container backend         Started  
 ✔ Container frontend        Started 
 ```
Then access this URL on your browser:
 ```
 http://localhost:4003
 ```

To stop the project:
```bash
docker compose down
```

To remove all images whenever you don't want to store them in local (require re-build when run the build command, that take time)

```bash
docker rmi -f $(docker images -q)
```
