## Singularity is a way to localize things - say allow users to download the program along with all dependencies and the OS needed for correct executionin the specific versions that would work perfectly well together.

### Singularity Image File - .sif format - is what you download to run a Singulaity container

This code downloads a playful container from a library online to your current directory
```bash
singularity pull library://godlovedc/funny/lolcow
```

Singularity was designed to work with Docker images, so you don’t have to rebuild containers from scratch. So note that you can download the Docker version of this same container from Docker Hub with the following command:
```bash
singularity pull docker://godlovedc/lolcow
```
Doing so may produce an error if the container already exists.

## You can run singularity containers from inside the new shell or outside of it.

### Entering the shell:
```bash
singularity shell lolcow_latest.sif
```

You will see this come up:
Singularity> 

However, you still will see your computer and your user even in this shell.

Singularity> whoami
dave
Singularity> hostname
hal-9000

Inside the container you can run commands that the image supports. For example:
```bash
cowsay moo
```

To exit the shell you run
```bash
exit
```

And the commands that are onl available inside the container would no longer run.

### To run container from the outside (not entering the shell):
```bash
singularity run lolcow_latest.sif
```

So what actually happens when you run a container? There is a special file within the container called a runscript that is executed when a container is run. You can see this (and other meta-data about the container) using the inspect command.
$ singularity inspect --runscript lolcow_latest.sif
#!/bin/sh

    fortune | cowsay | lolcat

Because Singularity containers have pre-defined actions that they must carry out when run, they are actually executable. 
$ ./lolcow_latest.sif

## Pipes:
Singularity does not try to isolate your container completely from the host system. This allows you to do some interesting things. For instance, you can use pipes and redirection to blur the lines between the container and the host system.

### Piping from singulairty to save files locally:
```bash
singularity exec lolcow_latest.sif cowsay moo > cowsaid
```

### pipe things into the container
```bash
cat cowsaid | singularity exec lolcow_latest.sif cowsay -n
```

### pipe things into another command inside of container:
$ singularity exec lolcow_latest.sif sh -c "fortune | cowsay | lolcat"

Why the trouble of sh -c?

Because if you run
singularity exec lolcow_latest.sif fortune | cowsay
This happens: Command 'cowsay' not found, but can be installed with:

To make all commands run inside the container, you need to:
1) Start a shell inside the container, and
2) Pass the full command pipeline as a quoted string, so the host shell doesn’t interpret the pipe.

Let’s break it down:

singularity exec lolcow_latest.sif – Run something inside the container.
sh -c "..." – Start a new shell inside the container.
"fortune | cowsay | lolcat" – Run this entire pipeline inside that shell.
