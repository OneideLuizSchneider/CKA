#### Multi Container PODs

- There are 3 patterns:
  - sidecar 
  - adapter
  - ambassador

- Sidecar:
  - Create 2 containers in a POD and sharing a volume, different mounthPaths but the same shared folder:
    ```
    apiVersion: v1
    kind: Pod
    metadata:
      name: two-containers
    spec:

      volumes:
      - name: shared-data
        emptyDir: {}

      containers:

      - name: nginx-container
        image: nginx
        volumeMounts:
        - name: shared-data
          mountPath: /usr/share/nginx/html

      - name: debian-container
        image: debian
        volumeMounts:
        - name: shared-data
          mountPath: /pod-data
        command: ["/bin/sh"]
        args: ["-c", "echo Hello from the debian container > /pod-data/index.html"]
    ```

- Doc:
  - <https://kubernetes.io/docs/tasks/access-application-cluster/communicate-containers-same-pod-shared-volume/>