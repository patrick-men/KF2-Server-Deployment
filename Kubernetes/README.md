# KF2 Server - Kubernetes

Here you will find how to deploy the server by using kubernetes.

## Requirements

In order for this to work, there are some mostly technical requirements:

- Have access to a kubernetes cluster - that can be kind, minikube, k8s or even something hosted by AWS or Google
- Linux and kubernetes knowledge
- Access to your router settings

## How-To

After cloning this repo, you will need to make some small changes to the config files. Specifically, check out the `storage.yaml` files - the lines that need to be changed are commented.
Using 50GB is recommended, as it allows you to add workshop maps without having to bother with space for a while - the more you use, the better tho.

Next, run the following commands.

```bash

cd Kubernetes/k8s-deployment
kubectl create ns kf2-server
kubectl apply -f .
```

The installation may take some time - to see how it's progressing, run `kubectl get pods -n kf2-server`, copy the name and then run `kubectl logs -f <pod-name> -n kf2`.

Once it's done, you should see something along the lines of `DevOnline: Sending out playfab requests...`. At this point the server is up and running.

For people to connect, you now need to expose the ports:

### Port-Forwarding

The method in this repo uses NodePort to expose the clusters ports to your host device - as such, the ports you need to look for are in the range of 30000-32768. To find the correct ports, you can run `kubectl get svc -n kf2-server`. You should see the NodePort, and the respective ports:

![NodePort-Ports](./old_repo_content/port-forwarding-example.png)

In this example, the ports are 31992 and 31111. This means you need to port-forward to those ports - look up your routers manual in order to do this properly.

### Joining the server

With everything set up, you now need to do the following in-game:

- F3
- `open <public-ip>:<port>`
