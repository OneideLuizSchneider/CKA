#### Daemon Sets

- Ensures a copy of the pod is always present in all your cluster nodes.
- Use cases:
  - Metrics/Logs Collectors
  - Network solutions

Example:
```
apiVersion: apps/v1
kind: Daemonset
metadata:
  labels:
    app: my-log-collector
  name: my-log-collector
spec:
  selector:
    matchLabels:
      app: my-log-collector
  template:
    metadata:
      labels:
        app: my-log-collector
    spec:
      containers:
      - image: my-log-collector:v1
        name: my-log-collector
```