# KF2 Server

This repo collects a few methods for deploying a Killing Floor 2 server. **The methods chosen are all based on containerisation**, and make use of images provided by `LinuxGSM`.

You will find a README/How-To for the following methods:

- Kubernetes (works on k8s, kind, minikube, etc.)
- Helm
- Docker
- Docker-Compose

> :warning: Note that you will need to port-forward in order for people to be able to join your server. Do this at your own risk, and make sure to know what the possible consequences of port-forwarding are! :warning:

### Note regarding LinuxGSM

*Most of the files provided in this repo can be changed to be used for the deployment of other servers, given there being an image provided by LinuxGSM.*