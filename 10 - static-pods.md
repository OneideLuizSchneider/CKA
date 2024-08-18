#### Static PODs

- Static PODs are created by KUBELET in the manifest directory.
  - Basically you can add a pod manifest in /etc/kubernetes/manifests and KUBELET will create that POD.

- In the worker nodes, you will find the the KUBELET config file in:
  - `ssh root@node-name or private IP`
  - `cd /var/lib/kubelet/config.yaml`
  - Field: `staticPodPath: /etc/...`
