# Welcome Fellows

## Purpose
This repository is home to the configuration files for Samuel Gross' personal kubernetes cluster. 

The primary purpose of the cluster is to replace paid services, such as streaming platforms, cloud storage, and ad blockers with locally run, open source solutions.

## Node Information
This kubernetes config is currently opitimized for a single node setup, but it could scale up to a larger environment with minor adjustments

The project is currently deployed on an Ubuntu LTS server instance running on a gaming pc from 2016. 
It only uses about 25% of resources unless decoding video, so everything is pretty lightweight, and this would likely run without issue on a much weaker pc.

The node is also running a cloudflared tunnel vpn that allows client devices to access the cluster from anywhere on the internet, but no ports are forwarded directly to the public internet. 
However, this config would be completely safe to expose to the public internet on ports 80 and 443 given the tight-knit ingress rules.


# Quick Reference

When working on this project, there will be some common commands that I will leave here for quick reference. 

Once connected to the cloudflared one client, run
```bash
ssh samuel@192.168.0.102
```

This project will be saved under /users/samuel/manifests, so to update the manifests before applying them, simply run

```bash
cd ~/manifests
git pull
```

To apply a manifest, run

```bash
kubectl apply -f manifest.yaml
```

To check the status of a resource, run 

```bash
kubectl get pods # or namespaces, services, deployments, ingress, etc.
# add -o yaml to end to generate yaml or -o json for json
```
or 
```bash
kubectl describe pod pod-name # resource resource-name
```


