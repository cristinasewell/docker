## DOCKER
---

# Before learning about DOCKER - what are VMs?
- Virtual computers or software-defined computers
- Instead of installing an operating system, install a hypervisor
    - divide your server resources into multiple servers
    - Ex: VMWare
- my WSL is build with a Linux kernel running in a lightweight virtual machine environment
- VM is virtualizing hardware

# DOCKER - is different
- Install only one operating system on your server
- Docker is virtualizing Operating System
- Doker (process running - daemon) 
- Containers 
    - very fast lightweight microcomputers:
        - they have their own memory
        - they're own cpu
        - os
        - network - so they are isolated and secure
    - lightweight and very fast

- Docker container or an image has all the dependencies packaged together, with all the settings and dependencies.

- You can move these docker images to other OSs

- You can only install windows based containers on windows based system, same for linux.



`Linode` - docker Lab - you can get some experience with docker there if you don't have it install on your computer

> **_Ex: - install a CentOS docker contaienr_**

```bash
# install CentOS

# download CentOS
# goes to the docker hub which is a registry of docker images
# these images are what we used to run or create our containers
docker pull centos

# --name to name the container
# centos - the image that i want to use
docker run -d -t --name mycentos centos

# see the running containers
docker ps

# connect to this CentoOS and test it
# bash - connect to the bash shell
docker exec -it containerName bash

# to get out of there
exit
```

> **_Ex: - install Alpine (other linux distribution)_**

```bash
docker pull alpine
docker -t -d --name myalpine alpine
docker ps
# connect to the shell
docker exec -it myalpine sh
# exit
exit
```

- We can use a specific tag/version of the docker image

> **_Ex: - install an image from docker hub_**

- Go to https://hub.docker.com/
- Find the image you're looking for:
    - `thenetworkchuck/nccoffee`
    - pull this image with a specific tag on your computer
    - ```bash
        # frenchpress is a specific tag
        docker pull thenetworkchuck/ncoffee:frenchpress

        # run it
        # -p - port 80:80 - map it from the container to our host
        # 80:80 (docker:host)
        docker run -t -d -p 80:80 --name nccoffee thenetworkchuck/ncoffee:frenchpress
        # see if it is running
        docker ps

        # you can see the website nccoffee by opening it in a browser

      ```

> **_Stop, Start any  Container and Stats_**

```bash
# stop container named myalpine
docker stop myalpine
# start container named myalpine
docker start myalpine
# see some stats 
docker stats
ctr+c # to get out of there
```

> **_Other Commands_**

```bash
docker container ls [OPTIONS]

--all , -a 	    #	Show all containers (default shows just running)
--filter , -f 	#	Filter output based on conditions provided
--format 	    #	Pretty-print containers using a Go template
--last , -n     #	-1 	Show n last created containers (includes all states)
--latest , -l   #		Show the latest created container (includes all states)
--no-trunc 		#   Don't truncate output
--quiet , -q 	#	Only display container IDs
--size , -s 	#	Display total file sizes

```

# Why DOCKER Containers?
---

- Portable
- Fast:
    - only needs one kernel
- You can use control groups 
- Isolated
- You can write your code, deploy it in a docker container and knwo that it works everywhere.
    - you can place everything that you need for your code in that container
    - so when you give your code to somebody else, you can give them the container with all dependencies and settings
- micro-services:
    - taking portions of your application and segment it
    - you can split your application in a few containers:
        - they would be isolated, when you update the application - you'll be updating only one container and so on...


Referenced:
https://www.youtube.com/watch?v=eGz9DS-aIeY



# Docker on WSL2
---
- Make sure you have WSL2 on your Windows
- Follow these steps for Docker
https://docs.docker.com/desktop/windows/wsl/

- On your WSL2 system check docker verison

```bash
docker --version
```

- If that works you should be ready to go :D



# Iron Bank (DOD) 
- **The DoD Centralized Artifacts Repository (DCAR) of hardened and centrally accredited containers:**
    - selecting, certifying, and securing best of breed development tools and software capabilities (over 170+ containers)
        - https://repo1.dsop.io/dsop/ (source code side)
        - https://ironbank.dsop.io (binary side)
- DevSecOps Collaboration Workspace
- Platform One
- Cloud One
- Zero-trust - using behavioral detections not only signatured based
