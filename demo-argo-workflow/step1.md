Install Argo workflow

```plain
kubectl get pod -n kube-system
```{{exec}}

```plain
kubectl create namespace argo
kubectl apply -f https://github.com/argoproj/argo-workflows/releases/download/v3.4.4/install.yaml
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
