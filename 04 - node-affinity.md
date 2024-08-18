#### Node Affinity

Example with 2 Node Labels:
```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    name: nginx
spec:
  containers:
  - name: nginx
    image: nginx
    ports:
    - containerPort: 80
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: size
            operator: In
            values:
            - Large
            - Medium


```

- Types:
  - requiredDuringSchedulingIgnoredDuringExecution
    - Node Label is Required
  - preferredDuringSchedulingIgnoredDuringExecution
    - Node Label is not Required, if not found will place it anywhere in the cluster
  - requiredDuringSchedulingRequiredDuringExecution
    - Node Label is Required and if the label is removed, it will remove the POD as well

If you only wanna check if the label exists `operator: Exists`, example:
- ```
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: size
            operator: Exists            
  ```



Official Doc.: <https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/>