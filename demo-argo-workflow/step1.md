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

Install argo cli
```plain
# Download the binary
curl -sLO https://github.com/argoproj/argo-workflows/releases/download/v3.4.4/argo-linux-amd64.gz

# Unzip
gunzip argo-linux-amd64.gz

# Make binary executable
chmod +x argo-linux-amd64

# Move binary to path
mv ./argo-linux-amd64 /usr/local/bin/argo

# Test installation
argo version
```{{exec}}