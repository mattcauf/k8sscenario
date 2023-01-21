
Welcome to your k8s cluster.

#Setup the env
Let's list some pods
```plain
kubectl get pod -n kube-system
```{{exec}}

### Solution
First we make sure we're in our home directory using
We are following https://argoproj.github.io/argo-workflows/quick-start/

```plain
kubectl create namespace argo
kubectl apply -f https://github.com/argoproj/argo-workflows/releases/download/v3.4.4/install.yaml
kubectl set-context --curent --namespace argo
```{{exec}}


```plain
kubectl patch deployment \
  argo-server \
  --namespace argo \
  --type='json' \
  -p='[{"op": "replace", "path": "/spec/template/spec/containers/0/args", "value": [
  "server",
  "--auth-mode=server"
]}]'
```{{exec}}



```plain
kubectl -n argo port-forward deployment/argo-server 2746:2746
```{{exec}}

Now access it via

[ACCESS ARGO]({{TRAFFIC_HOST1_2746}})