#Dockerfile

from ubuntu:16.04

RUN apt-get update && apt-get install curl -y

COPY script.txt .

CMD ["/bin/bash", "./script.txt"]


#Commands

docker build -t curler .
docker run -it curler