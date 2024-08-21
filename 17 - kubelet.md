## Troubleshooting tips

Pods are not scheduling or running:
- Take a look in kube-system:
  - `k get pod -n kube-system`
- Node and Pods Metrics:
  - `k top node`
  - `k top pod --containers=true`

Kubelet not running? Restart it:

- Check that the config is correct
  - `cat /etc/systemd/system/kubelet.service.d/10-kubeadm-conf`

- Check the logs
  - `journalctl -u kubelet`

- Restart
  - `systemctl restart kubelet`