#!/bin/bash

#Jenkins Installation

echo "Install Docker on...."
sudo apt update
sudo apt install -y docker.io

sudo systemctl enable docker
sudo systemctl start docker

docker --version
echo "Docker Installed"

echo "Creating Jenkins volume..."
docker volume create jenkins_home

echo "Starting Jenkins container..."
docker run -d \
  --name jenkins \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts

docker ps
echo "Jenkins Installed"

echo "Waiting for Jenkins to initialize..."
until docker exec jenkins test -f /var/jenkins_home/secrets/initialAdminPassword; do
  sleep 5
done

echo "Jenkins Initial Admin Password:"
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword

echo "Open Jenkins at:"
echo "http://<public-ip>:8080"






