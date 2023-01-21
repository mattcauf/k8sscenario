let's submit a workflow

```plain
argo submit -n argo --watch https://raw.githubusercontent.com/argoproj/argo-workflows/master/examples/hello-world.yaml
```{{exec}}


workflow is finish let's check the pod logs
```plain
kubectl get pod - n argo
```{{exec}}

now run kubectl logs PODNAME -n argo


Let's get the workflow file.
```plain
wget https://raw.githubusercontent.com/argoproj/argo-workflows/master/examples/hello-world.yaml
cat hello-world.yaml
```{{exec}}

