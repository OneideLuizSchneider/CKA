#### Labels and Selectors

- Filter PODs per label:
  - `kubectl get pods -l env=dev`
- PODs that are in more labels:
  - `kubectl get pods -l 'environment in (production),tier in (frontend)'`
  - `kubectl get pods -l 'env in (prod),bu in (finance),tier in (frontend)'`

- The labels in `selector.matchLabels` in the match the ones in the `template.metadata` labels, for example:
  - ```
      apiVersion: apps/v1
      kind: ReplicaSet
      metadata:
        name: replicaset-1
      spec:
        replicas: 1
        selector:
            matchLabels:
              tier: nginx
        template:
          metadata:
            labels:
              tier: nginx
          spec:
            containers:
            - name: nginx
              image: nginx
    ```