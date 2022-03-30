# Docker notes

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




## Looking at the container output
docker logs <container_name>

## Producing a sample error (typo in lose instead of less)
docker run --name example -d ubuntu bash -c "lose /etc/password"
docler logs example

_i.e._
```
ansalaza@ansalaza-HP-Notebook:~$ docker run --name example -d ubuntu bash -c "lose /etc/password"
20976d309a90f3b2030f204cc9f2485e5414b5ac2b5fa26d4bd2344033d97772
ansalaza@ansalaza-HP-Notebook:~$ docker logs example
bash: lose: command not found
```


---
## Stopping and Removing containers
### Killing and removing containers
docker kill <container_name>
docker rm <container_name>

_Example_
- On Terminal 1
docker run -it ubuntu bash

- On terminal 2
docker ps --format=$FORMAT

docker kill <container_name>

# Check the container status
docker ps --format=$FORMAT

# Check the status back on terminal 1 

---
# Example
ansalaza@ansalaza-HP-Notebook:~$ docker ps --format=$FORMAT

ID	9528ab4effdc
IMAGE	ubuntu
COMMAND	"bash"
CREATED	About a minute ago
STATUS	Up About a minute
PORTS	
NAMES	vigilant_jackson

ansalaza@ansalaza-HP-Notebook:~$ docker kill vigilant_jackson
vigilant_jackson
ansalaza@ansalaza-HP-Notebook:~$ docker ps --format=$FORMAT

# Terminal 1
ansalaza@ansalaza-HP-Notebook:~$ docker run -it ubuntu bash
root@9528ab4effdc:/# ansalaza@ansalaza-HP-Notebook:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
ansalaza@ansalaza-HP-Notebook:~$ docker rm vigilant_jackson
vigilant_jackson


---
# Resource constraints
# Memory limits
docker run --memory <maximum-allowed-memory> <image-name> command

# CPU limits
docker run --cpu-shares <relative to other containers>
docker run --cpu-quota <to limit in general>

# Notice Orchestration Generally requires resource limiting


# Lesons from the FIeld
- Don't let your container fetch dependencies when they start
- Dont' leave important things in unnamed stopped containers











