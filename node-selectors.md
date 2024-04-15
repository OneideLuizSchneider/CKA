#### Node Selectors

- Example:
  - `kubectl label nodes <node-name> <key>=<value>`
  - `kubectl label nodes worker01 size=large`

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
    
    nodeSelector:
      size: large
  ```
   