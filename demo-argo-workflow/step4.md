By using list_all_tickers.yaml and loop.yaml.
create a workflow that will calculate the mean for all tickers.

```plain
cat list_all_tickers.yaml 
```{{exec}}


```plain
argo submit -n argo --watch list_all_tickers.yaml
```{{exec}}


https://github.com/argoproj/argo-workflows/tree/master/examples
https://argoproj.github.io/argo-workflows/walk-through/output-parameters/
