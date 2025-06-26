# How to run as a kubectl plugin

## Requirements for operation

- kubectl installed and access to your Kubernetes cluster.
- Metrics Server must be running in the cluster (otherwise kubectl top will not work).
- Resource metrics (pods, nodes, etc.) are supported by Metrics Server.

## 1. Save this script to a file named `kubectl-kstats` (it's important that the name starts with `kubectl-`).

## 2. Make the file executable:

```bash
chmod +x kubectl-kstats
```

## 3.Place the file into a directory included in your $PATH, for example ~/bin (make sure ~/bin is in your $PATH):
```bash
mv kubectl-kstats ~/bin/
```
or add to PATH(example for bash):
```bash
export PATH=$PATH:$(pwd)
```

## 4. Now you can run the command as a plugin:
```bash
kubectl kstats pods kube-system
```
