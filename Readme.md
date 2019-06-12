# TK8 addon - Pumba

### What are TK8 addons?

- TK8 add-ons provide freedom of choice for the user to deploy tools and applications without being tied to any customized formats of deployment.
- Simplified deployment process via CLI (will also be available via TK8 web in future).
- With the TK8 add-ons platform, you can also build your own add-ons.

## What is Pumba?

Pumba is a tool by which we can perform Chaos Engineering experiments in containerized environments. Pumba is inspired by highly popular [Netflix Chaos Monkey](https://github.com/Netflix/SimianArmy/wiki/Chaos-Monkey) resilience testing tool for AWS cloud. Pumba takes a similar approach but applies it at the container level. It connects to the Docker daemon running on some machine (local or remote) and brings a level of chaos to it: “randomly” killing, stopping, and removing running containers.

## Prerequisites:

A Kubernetes cluster

## Get Started:

You can install Pumba on the Kubernetes cluster via TK8 addons functionality.

What do you need:
- tk8 binary

## Deploy Pumba on your Kubernetes Cluster:

Run:
```
$ tk8 addon install pumba
Search local for pumba
check if provided a url
Search addon on kubernauts space.
Cloning into 'pumba'...
Install pumba
apply pumba/main.yml
daemonset.extensions/pumba created
pumba installation complete
```
This command clones the https://github.com/kubernauts/tk8-addon-pumba repository locally and deploys Pumba as a daemonset.

## Test your Deployment:

For testing your deployment, simply list the pods which the daemonset has created. If all of them are in a Running state, then we've successfully initiated a chaos experiment.
```
$ kubectl get pods
NAME                                                              READY   STATUS      RESTARTS   AGE
pumba-g78f2                                                       1/1     Running     0          87s
pumba-mdslt                                                       1/1     Running     0          87s
pumba-qqxsv                                                       1/1     Running     0          87s
pumba-sbkxk                                                       1/1     Running     0          87s
pumba-xg84s                                                       1/1     Running     0          87s
```

## Chaos Testing:

The default deployment of Pumba starts chaos by randomly killing pods by sending a SIGKILL signal. However, this is trivial. For more sophisticated experiments like network delay, visit - https://github.com/alexei-led/pumba
**Note:** This project is quite young. So, things might be changing/breaking a bit.

## Uninstall Pumba:

For removing Pumba from your cluster, we can use TK8 addon's destroy functionality. Run:
```
$ tk8 addon destroy pumba
Search local for pumba
Addon pumba already exist
Found pumba local.
Destroying pumba
delete pumba from cluster
daemonset.extensions "pumba" deleted
pumba destroy complete
```
