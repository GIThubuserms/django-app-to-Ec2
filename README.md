# Simple Notes App for Deployment Purposes
This is a simple notes app built with React and Django.
Deployed using Docker on Ec2 with jenkins

## Requirements
1. Python 3.9
2. Node.js
3. React
4. Vscode

## Installation
1. Clone the repository
```
git clone https://github.com/LondheShubham153/django-notes-app.git
```

2. Build the app using docker
```
docker build -t notes-app .
```

3. Run the app using docker
```
docker run -d -p 8000:8000 notes-app:latest
```

## Nginx

Install Nginx reverse proxy to make this application available

`sudo apt-get update`
`sudo apt install nginx`
