# Getting Started with Docker

## 1.0 Introduction

The core of Docker is made of the Docker engine, a single-host software daemon that
allows us to create and manage containers.

## 1.1 Installing Docker on Ubuntu 14.04

## 1.2 Installing Docker on CentOS 6.5

## 1.3 Installing Docker on CentOS 7

## 1.4 Setting Up a Local Docker Host by Using Vagrant

Downloaded Vagrant from: https://www.vagrantup.com

VirtualBox is already installed.

Following: https://docs.vagrantup.com/v2/getting-started/index.html

    dc_1_04$ vagrant up
    Bringing machine 'default' up with 'virtualbox' provider...
    ==> default: Box 'hashicorp/precise32' could not be found. Attempting to find and install...
        default: Box Provider: virtualbox
        default: Box Version: >= 0
    ==> default: Loading metadata for box 'hashicorp/precise32'
        default: URL: https://atlas.hashicorp.com/hashicorp/precise32
    ==> default: Adding box 'hashicorp/precise32' (v1.0.0) for provider: virtualbox
        default: Downloading: https://atlas.hashicorp.com/hashicorp/boxes/precise32/versions/1.0.0/providers/virtualbox.box
    ==> default: Successfully added box 'hashicorp/precise32' (v1.0.0) for 'virtualbox'!
    ==> default: Importing base box 'hashicorp/precise32'...
    ==> default: Matching MAC address for NAT networking...
    ==> default: Checking if box 'hashicorp/precise32' is up to date...
    ==> default: Setting the name of the VM: dc_1_04_default_1451484586025_36751
    ==> default: Clearing any previously set network interfaces...
    ==> default: Preparing network interfaces based on configuration...
        default: Adapter 1: nat
    ==> default: Forwarding ports...
        default: 22 (guest) => 2222 (host) (adapter 1)
    ==> default: Booting VM...
    ==> default: Waiting for machine to boot. This may take a few minutes...
        default: SSH address: 127.0.0.1:2222
        default: SSH username: vagrant
        default: SSH auth method: private key
        default:
        default: Vagrant insecure key detected. Vagrant will automatically replace
        default: this with a newly generated keypair for better security.
        default:
        default: Inserting generated public key within guest...
        default: Removing insecure key from the guest if it's present...
        default: Key inserted! Disconnecting and reconnecting using new SSH key...
    ==> default: Machine booted and ready!
    ==> default: Checking for guest additions in VM...
        default: The guest additions on this VM do not match the installed version of
        default: VirtualBox! In most cases this is fine, but in rare cases it can
        default: prevent things such as shared folders from working properly. If you see
        default: shared folder errors, please make sure the guest additions within the
        default: virtual machine match the version of VirtualBox you have installed on
        default: your host and reload your VM.
        default:
        default: Guest Additions Version: 4.2.0
        default: VirtualBox Version: 5.0
    ==> default: Mounting shared folders...
        default: /vagrant => /Users/gnperdue/Dropbox/Programming/Programming/Docker/DockerCookbook/dockercCha01/dc_1_04

    dc_1_04$ vagrant ssh
    Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic-pae i686)
    
     * Documentation:  https://help.ubuntu.com/
     New release '14.04.3 LTS' available.
     Run 'do-release-upgrade' to upgrade to it.
    
    Welcome to your Vagrant-built virtual machine.
    Last login: Fri Sep 14 06:22:31 2012 from 10.0.2.2
    vagrant@precise32:~$ which python
    /usr/bin/python
    vagrant@precise32:~$ python --version
    Python 2.7.3
    vagrant@precise32:~$ exit
    logout
    Connection to 127.0.0.1 closed.
    dc_1_04$ vagrant destroy
        default: Are you sure you want to destroy the 'default' VM? [y/N] y
    ==> default: Forcing shutdown of VM...
    ==> default: Destroying VM and associated drives...

Back to the Cookbook for now...

    supervisor$ pwds
    ...1/dc_1_15/supervisor/
    supervisor$ ls
    Dockerfile           Vagrantfile          supervisord.conf
    README.md            docker-bootstrap.sh  wp-config.php

    supervisor$ vagrant up
    Bringing machine 'default' up with 'virtualbox' provider...
    ==> default: Box 'ubuntu/trusty64' could not be found. Attempting to find and install...
    Bringing machine 'default' up with 'virtualbox' provider...
    ==> default: Checking if box 'ubuntu/trusty64' is up to date...
    ==> default: VirtualBox VM is already running.

Then...

    supervisor$ vagrant ssh
    Welcome to Ubuntu 14.04.3 LTS (GNU/Linux 3.13.0-74-generic x86_64)
    ...
    Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
    applicable law.
    
    vagrant@vagrant-ubuntu-trusty-64:~$ docker ps
    The program 'docker' is currently not installed. To run 'docker' please ask your administrator to install the package 'docker'
    vagrant@vagrant-ubuntu-trusty-64:~$ ls
    vagrant@vagrant-ubuntu-trusty-64:~$

Hmmm, so `docker` was not set up. May have timed out at a bad time during set up
(I ran an errand.) Try again... `vagrant destroy`, then...

    supervisor$ vagrant up
    Bringing machine 'default' up with 'virtualbox' provider...
    ==> default: Importing base box 'ubuntu/trusty64'...
    ...
    ==> default: Adding user vagrant to group docker
    ==> default: docker.io: unrecognized service
    The SSH command responded with a non-zero exit status. Vagrant
    assumes that this means the command failed. The output for this command
    should be in the log above. Please read the output to determine what
    went wrong.

Hmmm. Well,

    supervisor$ vagrant ssh
    Welcome to Ubuntu 14.04.3 LTS (GNU/Linux 3.13.0-74-generic x86_64)
    ...
    vagrant@vagrant-ubuntu-trusty-64:~$ docker ps
    CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
    vagrant@vagrant-ubuntu-trusty-64:~$

Well, it looks like it worked anyway.

## 1.5 Installing Docker on a Rasberry Pi

## 1.6 Installing Docker on OS X Using Docker Toolbox

[Docker Toolbox](https://www.docker.com/docker-toolbox) allows us to start a
tiny virtual machine in Virtual Box that runs the Docker daemon. The Docker
client installed on the Mac is configured to to connect to that daemon.
We also have `docker-compose`.

    docker-machine start dev
    eval "$(docker-machine env dev)"
    docker-machine ls

We can `ssh` to the vm:

    dockercCha01$ docker-machine ssh dev
                            ##         .
                      ## ## ##        ==
                   ## ## ## ## ##    ===
               /"""""""""""""""""\___/ ===
          ~~~ {~~ ~~~~ ~~~ ~~~~ ~~~ ~ /  ===- ~~~
               \______ o           __/
                 \    \         __/
                  \____\_______/
     _                 _   ____     _            _
    | |__   ___   ___ | |_|___ \ __| | ___   ___| | _____ _ __
    | '_ \ / _ \ / _ \| __| __) / _` |/ _ \ / __| |/ / _ \ '__|
    | |_) | (_) | (_) | |_ / __/ (_| | (_) | (__|   <  __/ |
    |_.__/ \___/ \___/ \__|_____\__,_|\___/ \___|_|\_\___|_|
    Boot2Docker version 1.8.3, build master : af8b089 - Mon Oct 12 18:56:54 UTC 2015
    Docker version 1.8.3, build f4bf5c7
    docker@dev:~$
    docker@dev:~$ uname -a
    Linux dev 4.1.10-boot2docker #1 SMP Mon Oct 12 18:36:49 UTC 2015 x86_64 GNU/Linux

We can see that when we do, `Boot2Docker` is there "under the hood."

## 1.7 Using `Boot2Docker` to Get a Docker Host on OS X

Prefer Docker Toolbox...

`Boot2Docker` is a lightweight Linu distribution based on Tiny Core Linux and
configured specifically to act as a Docker host. The Docker client runs on OS X
(unlike the daemon) and is set up on the local machine.

## 1.8 Running `Boot2Docker` on Windows 8.1 Desktop

Oy.

## 1.9 Starting a Docker Host in the Cloud by Using Docker Machine

AWS, DigitalOcean, Azure, Google Compute Engine, etc.

## 1.10 Using Docker Experimental Binaries

## 1.11 Running Hello World in Docker

    dockercCha01$ docker run busybox echo hello world
    hello world

(I have `busybox` in my images set already.)

Containers are based on images, and an image needs to be passed to `docker run`.
Here we specify an image called `busybox`. If you don't have an image, Docker
will pull it from a public registry (a catalog of Docker images that the client
can communicate with and download images from).

    dockercCha01$ docker run -t -i ubuntu:14.04 /bin/bash
    root@8e209a76f785:/#

Here, `-t -i` let us use the interactive prompt correctly.

## 1.12 Running a Docker Container in Detached Mode

How do we run a service in the background? We use the `-d` option for `docker run`.

    dockercCha01$ docker run -d -p 1234:1234 python:2.7 python -m SimpleHTTPServer 1234
    Unable to find image 'python:2.7' locally
    2.7: Pulling from library/python
    
    9ee13ca3b908: Pull complete
    23cb15b0fcec: Pull complete
    5e5f21412e19: Pull complete
    df82ac64861d: Pull complete
    a06b823c6a02: Pull complete
    0b2ad41b6195: Pull complete
    93a5505ac7f7: Pull complete
    78fef92ba578: Pull complete
    fefe045f942e: Pull complete
    237b75df8e1d: Pull complete
    032cdf487b54: Pull complete
    f2efebaea0bf: Pull complete
    7436fc1e0756: Pull complete
    Digest: sha256:b2867bf4c20ca840bb28075cbca1ceba3e084d48aacea3d34196d3cb3b443fdb
    Status: Downloaded newer image for python:2.7
    68b9d7d7064ea99267fe75f0509f5b09a35bb646c37f425ecd0535f18315eefc
    dockercCha01$ docker ps
    CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
    68b9d7d7064e        python:2.7          "python -m SimpleHTTP"   58 seconds ago      Up 55 seconds       0.0.0.0:1234->1234/tcp   elegant_hodgkin

`-d` causes the container to run in the background. We can connect to it by using
`exec` and running a bash shell:

    dockercCha01$ docker exec -ti 68b9d7d7064e /bin/bash
    root@68b9d7d7064e:/# ps -ef | grep python
    root         1     0  0 22:25 ?        00:00:00 python -m SimpleHTTPServer 1234
    root        14     8  0 22:28 ?        00:00:00 grep python

## 1.13 Creating, Starting, Stopping, and Removing Containers

Use `create`, `start`, `stop`, `kill`, and `rm`. Examine them with, e.g.

    dockercCha01$ docker stop --help
    
    docker stop [OPTIONS] CONTAINER [CONTAINER...]
    
    Stop a running container by sending SIGTERM and then SIGKILL after a
    grace period
    
      --help=false       Print usage
      -t, --time=10      Seconds to wait for stop before killing itUsage:

We can "stage" containers with `docker create`.

    dockercCha01$ docker ps
    CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
    68b9d7d7064e        python:2.7          "python -m SimpleHTTP"   10 minutes ago      Up 10 minutes       0.0.0.0:1234->1234/tcp   elegant_hodgkin
    dockercCha01$ docker stop elegant_hodgkin
    elegant_hodgkin
    dockercCha01$ docker ps
    CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

## 1.14 Building a Docker Image with a Dockerfile

A _Dockerfile_ is a text file that describes the steps Docker must take to prepare
an image.

For example, create a `Dockerfile` in an empty working directory:

    dockercCha01$ mkdir dc_1_14
    dockercCha01$ cd dc_1_14/
    dc_1_14$ vim Dockerfile
    dc_1_14$ more Dockerfile
    FROM busybox
    ENV foor=bar
    dc_1_14$ docker build -t busybox2 .
    Sending build context to Docker daemon 2.048 kB
    Step 0 : FROM busybox
    ---> 2c5ac3f849df
    Step 1 : ENV foor bar
    ---> Running in 83bb36621980
    ---> d5234fe60022
    Removing intermediate container 83bb36621980
    Successfully built d5234fe60022
    dc_1_14$ docker images
    REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
    busybox2            latest              d5234fe60022        58 seconds ago      1.113 MB
    ...
    busybox             latest              2c5ac3f849df        8 weeks ago         1.113 MB

We may now use `Docker images` to see the new imges:

    dc_1_14$ docker run busybox2 env | grep foo
    foor=bar

## 1.15 Docker Supervisor to Run WorDress in a Single Container

    dc_1_15$ cp -r ../../docbook/ch01/supervisor ./supervisor
    dc_1_15$ ls supervisor/
    Dockerfile           Vagrantfile          supervisord.conf
    README.md            docker-bootstrap.sh  wp-config.php

...

## 1.18 Sharing Data in Your Docker Host with Containers

Use, for example `-v "$PWD":/dirname`:

    Tutorials$ pwd
    /Users/perdue/Dropbox/ArtificialIntelligence/TensorFlow/Tutorials
    Tutorials$ docker run -it -v "$PWD":/mnist b.gcr.io/tensorflow/tensorflow:latest-devel
    root@452eb87bbb22:~# ls
    root@452eb87bbb22:~# pwd
    /root
    root@452eb87bbb22:~# ls /mnist
    root@452eb87bbb22:~# cd /mnist
    root@452eb87bbb22:/mnist#

By default, Docker mounts the volume in read-write mode.
