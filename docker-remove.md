docker system prune will delete ALL dangling data (i.e. In order: containers stopped, volumes without containers and images with no containers). Even unused data, with -a option.

You also have:

    sudo docker container prune
    sudo docker image prune
    sudo docker network prune
    sudo docker volume prune

For unused images, use docker image prune -a (for removing dangling and ununsed images).
Warning: 'unused' means "images not referenced by any container": be careful before using -a.

As illustrated in A L's answer, docker system prune --all will remove all unused images not just dangling ones... which can be a bit too much.


Refer (again) to VonC, using the even more recent system prune. The impatient can skip the prompt with the -f, --force option:

docker system prune -f

The impatient and reckless can additionally remove "unused images not just the dangling ones" with the -a, --all option:
```
docker system prune -af
```

