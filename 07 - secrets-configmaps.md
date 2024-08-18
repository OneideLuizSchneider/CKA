
- ConfigMap example:
```
apiVersion: v1
kind: Pod
metadata:
  name: configmap
spec:
  containers:
  - name: configmap-container
    image: nginx
    env:
    - name: CONFIGMAP_NAME
      valueFrom:
        configMapKeyRef:
          name: myconfigmap
          key: name
```

- Secrets:
  kubectl create secret generic mysecrets --from-literal=username='my-user' --from-literal=password='39528$vdg7Jb'


```
apiVersion: v1
kind: Pod
metadata:
  name: multiple-secrets
spec:
  containers:
  - name: envars-test-container
    image: nginx
    env:
    - name: BACKEND_USERNAME
      valueFrom:
        secretKeyRef:
          name: mysecrets
          key: username
    - name: BACKEND_PASS
      valueFrom:
        secretKeyRef:
          name: mysecrets
          key: password
```

- OR:

```
apiVersion: v1
kind: Pod
metadata:
  name: envfrom-secret
spec:
  containers:
  - name: containername
    image: nginx
    envFrom:
    - secretRef:
        name: mysecrets
```