#### Command and Args Example:

- k8s Deployment:
```
apiVersion: v1
kind: Pod
metadata:
  name: ubuntu
  labels:
    purpose: ubuntu
spec:
  containers:
  - name: ubuntu
    image: ubuntu
    command: ["sleep"]
    args: ["5000"]
```

- Dockerfile:
```
FROM ubuntu
ENTRYPOINT: ['sleep']
CMD ['5']
```