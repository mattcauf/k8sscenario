let's submit a workflow

```plain
git clone https://github.com/mattcauf/k8sscenario.git
cd k8sscenario/worklow
argo submit -n argo --watch sample-python.yaml
```{{exec}}


workflow is finish let's check the pod logs
```plain
kubectl get pod - n argo
```{{exec}}

now run kubectl logs PODNAME -n argo


Let's get the workflow file.
```plain
cat sample-python.yaml
```{{exec}}

