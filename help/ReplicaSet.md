#### Examples:

```
apiVersion: apps/v1

kind: ReplicaSet

metadata:
  name: my-rs
  namespace: default
  labels:
    app: myapp


spec:
  template:
    metadata:
      name: my-rs      
      labels:
        app: myapp
    spec:
      containers:
      - name: nginx
        image: nginx:latest
  
  replicas: 2
  selector:
    matchLabels:
      app: myapp


```