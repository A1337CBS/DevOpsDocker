#Dockerfile

from ubuntu:16.04

RUN apt-get update && apt-get install curl -y

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash

RUN apt install -y nodejs

COPY package.json package-lock.json ./

RUN npm install

COPY . .

RUN npm run build

RUN npm install -g serve

CMD ["serve", "-s", "-l","5000","dist"]

#Commands
docker build -t frontend .
docker container run -p 5000:5000 frontend

