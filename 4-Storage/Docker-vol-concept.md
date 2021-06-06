docker filesystem : /var/lib/docker
it contains volumes, containers, images(stored in layed arch)

volume mount - mount from default location of docker within the host 
bind mount - mount from specific location of host

VOLUME MOUNT
docker run -d \
  --name devtest \
  --mount source=myvol2,target=/app \
  nginx:latest

BIND MOUNT
docker run -d \
  --name=nginxtest \
  --mount source=nginx-vol,destination=/usr/share/nginx/html,readonly \
  nginx:latest  

Storage Driver --> Help manage storage on img/containers
Volume Driver --> local, 3rd party storage providers(cloud)
