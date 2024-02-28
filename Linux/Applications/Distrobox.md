
The internet wants me to use Distrobox over [[Toolbox|Toolbox]]


Make a new container

```
distrobox-create --name CONTAINER-NAME --image OS-NAME:VERSION

distrobox-create --name ubuntu --image docker.io/ubuntu:latest

```


enter the container
```shell
distrobox-enter <toolbox name>
```

install the app

export the icon
```shell
distrobox-export --app <app name>
```

show your existing containers
```
distrobox ls 
```