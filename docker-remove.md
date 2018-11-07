docker system prune will delete ALL dangling data (i.e. In order: containers stopped, volumes without containers and images with no containers). Even unused data, with -a option.

You also have:

    docker container prune
    docker image prune
    docker network prune
    docker volume prune

For unused images, use docker image prune -a (for removing dangling and ununsed images).
Warning: 'unused' means "images not referenced by any container": be careful before using -a.

As illustrated in A L's answer, docker system prune --all will remove all unused images not just dangling ones... which can be a bit too much.
