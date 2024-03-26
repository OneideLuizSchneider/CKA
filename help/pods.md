#### Examples:

```
apiVersion: v1

kind: Pod

metadata:
  name: nginx
  namespace: default
  labels:
    app: nginx


spec:

  containers:
  - name: nginx
    image: nginx:latest


```