
> Services need to run on all interfaces (like 0.0.0.0) and not just localhost.
<br>
> Services need to be accessible via HTTP and **not** HTTPS.

Run Nginx and expose the Pod:

```plain
kubectl run nginx --image=nginx:alpine
kubectl expose pod nginx --port 80 --name nginx
kubectl wait --for=condition=ready pod nginx
```{{exec}}

Then start kubectl forward:

```plain
kubectl port-forward --address 0.0.0.0 service/nginx 80:80
```{{exec}}

Now access it via

[ACCESS NGINX]({{TRAFFIC_HOST1_80}})

It's also possible to access ports using the top-right navigation in the terminal.
Or we can display the link to that page:

[ACCESS PORTS]({{TRAFFIC_SELECTOR}})

```plain
kubectl get pod -n kube-system
```{{exec}}

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
kubectl -n argo --address 0.0.0.0 port-forward deployment/argo-server 8080:2746
```{{exec}}
