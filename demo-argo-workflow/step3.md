Doing some optimization

```plain
cat loop.yaml
```{{exec}}

lets submit it
```plain
argo submit -n argo --watch loop.yaml
```{{exec}}

In another tab run


Let's get the workflow file.
```plain
watch kubectl get pod -n argo
```{{exec}}

We can now process an infinity of ticker