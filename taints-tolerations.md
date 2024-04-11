#### Taints and Tolerations

- Example:
  - `kubectl taint nodes worker01 disk=ssh:NoSchedule`
    - `NoSchedule` will not be schedule on it
  - `kubectl taint nodes worker01 disk=ssh:PreferNoSchedule`
    - `PreferNoSchedule` will try to avoid schedule on it
  - `kubectl taint nodes worker01 disk=ssh:NoExecute`
    - `NoExecute` will evict all the pods that don't have the taint
- Remove taint:
  - `kubectl taint nodes worker01 disk=ssh:NoExecute-`
  
- POD:
  ```
  apiVersion: v1
  kind: Pod
  metadata:
    name: nginx
  spec:
    containers:
    - name: nginx
      image: nginx
    tolerations:
    - key: "example-key"
      operator: "Exists"
      effect: "NoSchedule"
  ```