#### ETCDCTL

ETCD is a key-value database.


export ETCDCTL_API=3

Backup:
```
etcdctl \
  --endpoints=https://127.0.0.1:2379 \
  --cert=/etc/kubernetes/pki/etcd/server.crt \
  --key=/etc/kubernetes/pki/etcd/server.key \
  --cacert=/etc/kubernetes/pki/etcd/ca.crt \
  snapshot save /opt/snapshot-pre-boot.db
```

Restore:
```
etcdctl \
  snapshot restore \
  --data-dir /var/lib/etcd-from-backup \
             /opt/snapshot-pre-boot.db
```

Edit the ETCD manifest and change to the new folder `/var/lib/etcd-from-backup`:
- vi /etc/kubernetes/manifests/etcd.yaml


ssh into the controlPlane and copy the certs:
sudo scp -r /etc/kubernetes/pki/etcd/ root@node01:/root



Docs:
- <https://github.com/etcd-io/etcd>