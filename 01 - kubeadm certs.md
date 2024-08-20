#### kubeadm certs

- Check the expiration of all certs:
  - `kubeadm certs check-expiration`
- Renew All:
  - `kubeadm certs renew all`
- Renew only 1 at the time:
  - `kubeadm certs renew -h`
    - Under `Available Commands:` you'll see all components
  - `kubeadm certs renew <component>`

Doc: <https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-certs/>