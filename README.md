# Docker Demo

This repository demonstrates how to create a Docker container that runs a simple Python script.

## Steps to Create and Run the Docker Container

### Step 1: Install Docker

Ensure Docker is installed on your system. You can install Docker on Ubuntu by following these commands:

```sh
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world
# docker_demo


# Install Docker
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world

# Create project directory and files
mkdir my-docker-python-app
cd my-docker-python-app
echo 'print("Hello")' > main.py
echo -e "FROM python:3.9-slim\nWORKDIR /usr/src/app\nCOPY . .\nCMD [\"python\", \"main.py\"]" > Dockerfile
Dockerfile  main.py

# Build and run the Docker image
sudo docker build -t my-python-app .
sudo docker run my-python-app

