# Running Docker images

## Install a new image and run it
>```
> docker run docker/whalesay
>```


_If the image iis no found locally it pulls it, and after runs it_


## Remove image after running it

>```
> docker run --rm -it ubuntu sleep 5
> docker run -it ubuntu bash -c "sleep 3; echo all done"
>```


## Running an image in detached mode
docker run -d -it \<image name> <command>


>```
> docker run -d -it ubuntu bash
>```

```
ansalaza@ansalaza-HP-Notebook:~$ docker run -d -it ubuntu bash
a425950336c2f81065dfca3218c3b4f00df373d8d166d6140142ac4d6a5a7cd7
```

```
ansalaza@ansalaza-HP-Notebook:~$ docker ps --format=$FORMAT

ID	a425950336c2
IMAGE	ubuntu
COMMAND	"bash"
CREATED	59 seconds ago
STATUS	Up 50 seconds
PORTS	
NAMES	compassionate_golick
```

_Where the environment FORMAT is set up like_

```
export FORMAT="\nID\t{{.ID}}\nIMAGE\t{{.Image}}\nCOMMAND\t{{.Command}}\nCREATED\t{{.RunningFor}}\nSTATUS\t{{.Status}}\nPORTS\t{{.Ports}}\nNAMES\t{{.Names}}\n"
```


## Jump in a conatiner in detached mode
docker attach \<names>

>```
> docker attach compassionate_golick
>```

## Jump out a container in detached mode
ctrl +p, ctrl + q

## List running containers
docker ps --format $FORMAT


## List all containers, running and not running
docker ps -a

## List last container
docker ps -l

## Running more commands inside a container (docker exec)
docker exec -it compassionate_golick bash


_When exiting from an attached container without the seqience keys `ctrl+p, ctrl+d` the container running dies._

