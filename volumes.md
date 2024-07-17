#### PersistentVolume and PersistentVolumeClaim

- POD, PV and PVC example with hostPath:
  ``` 
    apiVersion: v1
    kind: PersistentVolume
    metadata:
      name: pv-log
    spec:
      capacity:
        storage: 100Mi
      persistentVolumeReclaimPolicy: Retain
      hostPath:
        path: /pv/log
      accessModes:
        - ReadWriteMany
    
    ---
    
    apiVersion: v1
    kind: PersistentVolumeClaim
    metadata:
      name: pvc-log
    spec:
      volumeName: pv-log
      accessModes:
        - ReadWriteMany
      resources:
        requests:
          storage: 10Mi

    ---

    apiVersion: v1
    kind: Pod
    metadata:
      name: nginx
    spec:
      containers:
        - name: nginx
          image: nginx
          volumeMounts:
          - mountPath: "/var/www/html"
            name: mypd
      volumes:
        - name: mypd
          persistentVolumeClaim:
            claimName: pvc-log
  ```
- Doc: 
  - <https://kubernetes.io/docs/concepts/storage/persistent-volumes/>
  - <https://kubernetes.io/docs/concepts/storage/storage-classes/>