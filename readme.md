# Firing Up K8s Cluster

## Using Kind utility to generate the cluster. Kind allows us to generate lightweight k8s cluster upon docker which is ideal for lab env as well as local testing.


# Installation of Kind
## Prereq Go (V 1.17+) and Docker installed. Also make sure that go is available at system path or you can create symlink to /usr/local/bin.

## Once Go and Docker is installed you can install Kind using
```
go install sigs.k8s.io/kind@v0.17.0
```
## Above CMD will install kind as Go Addon. The binaries will be available at

```
$(go env GOPATH)/bin
```
## Either add it to the path or create a symlink. 
```
sudo ln -s $(go env GOPATH)/bin/kind /usr/local/bin/kind
```

## Once Kind is accessible through terminal fire up a cluster using

```
kind create cluster

```
## Note: Above CMD will install latest available k8s cluster which is v1.25 at the time.

## In order to Run A specific version run

```
kind create cluster --image "Cluster Image"
```

## Image Releases can be found at "https://github.com/kubernetes-sigs/kind/releases"

## You can also specify more configuration via YAML file which allows you to modify Cluster Endpoints like APIServer expose ports and specify nodes etc.

```
kind create cluster --config "Path to config.yaml"
```
