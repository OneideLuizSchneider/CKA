#### Encrypting Confidential Data at Rest


- Docs: 
  - <https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/>

- Look into a Secret with `ETCDCTL`:
  - ```
    ETCDCTL_API=3 etcdctl \
      --cacert=/etc/kubernetes/pki/etcd/ca.crt   \
      --cert=/etc/kubernetes/pki/etcd/server.crt \
      --key=/etc/kubernetes/pki/etcd/server.key  \
      get /registry/secrets/default/mysecret | hexdump -C
    ```