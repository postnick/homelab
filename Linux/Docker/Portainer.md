[Primary Link](https://docs.portainer.io/v/ce-2.9/start/install/server/docker/linux)

```shell
sudo docker volume create portainer_data
```

```shell
sudo docker run -d -p 8000:8000 -p 9443:9443 --name portainer \
	--restart=always \
	-v /var/run/docker.sock:/var/run/docker.sock \
	-v portainer_data:/data \
	portainer/portainer-ce:latest
```

How to Update to a newer version:
```shell
sudo docker stop portainer && sudo docker rm portainer

docker pull portainer/portainer-ce:latest
```

Once the Stop/RM is o ver please re runn the Docker Run command 2 sections up. 

https://localhost:9443

