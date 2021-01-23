#Commands
docker pull devopsdockeruh/first_volume_exercise
touch log.txt
docker container run -v "$(pwd)/log.txt:/usr/app/logs.txt" devopsdockeruh/first_volume_exercise
