#### ETCD

- ETCD stores info from:
  - Nodes
  - PODs
  - Configs
  - Secrets
  - Accounts
  - Roles
  - Bindings
  - Others...

- Some commands:
  - etcdctl snapshot save 
  - etcdctl endpoint health
  - etcdctl get
  - etcdctl put

- bkp and restore:
  - ./backup-restore.md

- to check if the conf is external:
  - go to /etc/kubernetes/manifests/
  - open the file `kube-apiserver.yaml`
    - and look for `--etcd-servers=https://some-ip:2379`

- Check conf from a etcd-server:
  - `ps -ef | grep etcd`

- List Cluster Nodes:
  - etcdctl \
      --endpoints=https://127.0.0.1:2379 \
      --cert=/etc/etcd/pki/etcd.pem \
      --key=/etc/etcd/pki/etcd-key.pem  \
      --cacert=/etc/etcd/pki/ca.pem \
      member list
