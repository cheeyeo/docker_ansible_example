boot2docker init

boot2docker start

$(boot2docker shellinit)

#!/bin/bash
# Delete all containers
docker rm $(docker ps -a -q)
# Delete all images
docker rmi $(docker images -q)

docker ps -q |xargs docker rm

docker images -q |xargs docker rmi
