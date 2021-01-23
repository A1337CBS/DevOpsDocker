docker container run -d --rm -it --name looper-it ubuntu:16.04 sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
docker container exec -it looper-it bash
apt update
apt install curl 
exit
docker container attach looper-it
helsinki.fi