# Hosting a Static Website on Docker

This repository demonstrates how to host a static website using a Docker container. The website content is cloned from a GitHub repository and served using the Apache web server inside the container.

## Prerequisites

Before you begin, ensure you have Docker (Version 19.03 or later) installed: You can install Docker by following the official Docker installation guide.


## Project Structure
.
├── Dockerfile
├── README.md
└── (Web content cloned from GitHub)
- `Dockerfile`: The Dockerfile to build the Docker image.
- `README.md`: This file.
- The web content (HTML, CSS, JS) will be cloned from a GitHub repository.

## Steps to Run the Website

 # Create the Dockerfile
The Dockerfile will specify the environment setup and the steps for hosting your website.

**Dockerfile**:
FROM amazonlinux:latest

# Install dependencies
RUN yum update -y && \
    yum install -y httpd git  

# change directory
RUN cd /var/www/html

# Clone the repository
RUN git clone <github-repo-url> with the actual URL of the repository.

# copy files into html directory
RUN cp -R your repo name/. /var/www/html/

# remove unwanted folder
RUN rm -rf your repo name

# exposes port 80 on the container
EXPOSE 80

# set the default application that will start when the container start
ENTRYPOINT ["/usr/sbin/httpd", "-D", "FOREGROUND"]

# Build the Docker image:
To build the Docker image, run the following command:
docker build -t static-website . - replace static website with any name of your choice. 

# Run the Docker container:
docker run -d -p 8080:80 static-website
This will start the container in detached mode and map port 8080 on your host to port 80 inside the container (where Apache is serving the website).

# Access the website:
Open a web browser and visit http://localhost:8080 to view your static website.

# stop the container:
run the following commands 
docker ps
docker stop <container_id>
Replace <container_id> with the ID of the running container.