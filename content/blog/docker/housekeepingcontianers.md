


# Housekeeping containers


Nuclear option; remove all containers

```docker
$ docker ps -a -q | \
 xargs --no-run-if-empty docker rm -f
```

DANGER with above might remove non-running  data-only containers.

Removing  non running containers

```docker
docker ps -a -q --filter status=exited | \         1
 xargs --no-run-if-empty docker rm
```

Other options are running and restarting.

What about

```docker
docker container prune

```
 How does it differ ?


 Advanced use case List all nonzero error code

```docker
 comm -3 \
 <(docker ps -a -q --filter=status=exited | sort) \
 <(docker ps -a -q --filter=exited=0 | sort) | \
 xargs --no-run-if-empty docker inspect > error_containers
 ```
** Notes:**
1 comm command, compares the contents of two files. The -3 argument suppresses lines that appear in both files (in this example, those with a zero exit code) and outputs any others.
2 Finds exited container IDs, sorts them, and passes them as a file to comm
3 Finds containers with an exit code of 0, sorts them, and passes them as a file to comm
4 Runs docker inspect against containers with a nonzero exit code (as piped in by comm) and saves the output to the error_containers file

The <(command) syntax is called process substitution. It treats the output of a command as a file.


Make these one-liners available as commands

```
alias dockernuke='docker ps -a -q | \
xargs --no-run-if-empty docker rm -f'
```


## House keeping volumes

You do this typically to free disk space by orphaned  mounts

##  Dependency graph of your Docker images