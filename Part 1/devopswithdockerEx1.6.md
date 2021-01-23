#Dockerfile

from devopsdockeruh/overwrite_cmd_exercise

RUN chmod +x /usr/app/start.sh

ENTRYPOINT ["/usr/app/start.sh","-c", "1"]

#Commands

docker build -t docker-clock .
docker run -it docker-clock