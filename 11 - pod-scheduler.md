#### Manual Scheduler


Example:
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

  # manual set node
  nodeName: node01
```

To add a POD to a node just add the field `nodeName` with the node you wanna add the POD.