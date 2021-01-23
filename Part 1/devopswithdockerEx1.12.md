#Dockerfile - frontend
from ubuntu:16.04

RUN apt-get update && apt-get install curl -y

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash

RUN apt install -y nodejs

COPY package.json package-lock.json ./

RUN npm install

COPY . .

ENV API_URL http://localhost:8000

RUN npm run build

RUN npm install -g serve


CMD ["serve", "-s", "-l","5000","dist"]

#Commands - frontend
docker build -t frontend .
docker container run -p 5000:5000 frontend

#Dockerfile - backend
from ubuntu:16.04

WORKDIR /app

RUN apt-get update && apt-get install curl -y

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash

RUN apt install -y nodejs

COPY package.json package-lock.json ./

RUN npm install

COPY . .

ENV FRONT_URL http://localhost:5000

CMD ["npm", "start"]

#Commands - backend
touch log.txt
docker build -t backend .
docker run -p 8000:8000 -v "$(pwd)/logs.txt:/app/logs.txt" backend

