# Conair Kubernetes Container

Run systemd, etcd, kubernetes and docker in a container.

## Requirements

 * Conair

## Create a Kubernetes container

This is a short step-by-step example on how to create a Kubernetes container with conair. Downloading conair and the base image is the easiest option. But you can also build those yourself. Check the conair repository for instructions.

```
# fetch the latest conair binary
wget http://conair.teemow.com/bin/conair
chmod +x ./conair
alias conair="sudo $(pwd)/conair"

# initialize host setup
conair init

# create a base image
conair pull base

# create a coreos image
git clone https://github.com/teemow/conair-kubernetes
cd conair-kubernetes
conair build kubernetes

# run your kubernetes container
conair run kubernetes

# check if it is running
machinectl status kubernetes

# access your coreos (user: core, pass: coreos)
ssh core@$(conair ip kubernetes)
```

## kubecfg access from outside of the container

```
kubecfg -h="http://$(conair ip kubernetes):8080/" list /pods
```
