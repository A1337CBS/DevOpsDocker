#Dockerfile
from ubuntu:16.04

WORKDIR /app

RUN apt-get update && apt-get install curl -y

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash

RUN apt install -y nodejs

COPY package.json package-lock.json ./

RUN npm install

COPY . .


CMD ["npm", "start"]
#Commands
touch log.txt
docker build -t backend .
docker run -p 8000:8000 -v "$(pwd)/logs.txt:/app/logs.txt" backend

