
### Docker

Containers provide OS level virtualization, whereas VMs provide hardware virtualization.
Container shares the host system's kernel with other container.
Container run as isolated process in user space.


Docker is one of the provider of container service.
Docker Image which is running is called container.

```
sudo groupadd docker
sudo usermod -aG docker $USER
# logout and login
```

```
docker --version
docker info
```

Build Docker Image
```
docker build -t my_image_name:version_name -f ./path/to/Dockerfile .
```

Push Docker Image to Docker Hub
```
docker login
docker tag my_image_name dockerhub_id/image_name:version_name
docker push dockerhub_id/image_name
```

Pull Docker Image from Docker Hub
```
docker pull image_name:tag_name
```

Export/Import Docker Image locally
```
docker save image_name:tag_name | gzip > image_name_tag.tar.gz
docker load < image_name_tag.tar.gz
```

Running Docker Image
```
docker run [ --name my_container_name  ] image_name:tag
	   [ --rm		       ]
	   [ --net=host		       ]
	   [ -it		       ]
	   [ -p 7000:8000    # host_port:container_port	]
	   [ -v /path/to/host:/path/to/container ]
	   [ -d    # for detached mode ]
```

```
Ctrl+P+Q    # for switching from container terminal to host terminal
docker attach container_name # in place of container_name, container_id can also be used
docker container start container_name [-ia]
docker container stop container_name

docker container ls [--all]
docker container rm container_name
docker container rm $(docker container ls -a -q)
```

```
docker inspect container_name --format '{{.NetworkSettings.IPAddress}}'
```

```
docker image ls
docker image rm image_name
docker image rm $(docker image ls -a -q)
```

Other related stuffs
```
docker stats [container_name]
docker system df
docker system prune -a
```
