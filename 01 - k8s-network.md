#### k8s network

- To get IP(and more info... but...) from the Node:
  - `kubectl get node -o wide`
- Get network info:
  - `ip address`
  - `ifconfig`
- To see only the bridge interfaces:
  - `ip address show type brige`
- To look at ports:
  - `netstat --help`
  - `netstat -npl | grep ...`
  - See the kube-scheduler port:
    - `netstat -npl | grep scheduler`
- CNI
  - Default path:
    - `/opt/cni/...`
  - To see which CNI is in use:
    - `ls /etc/cni/net.d/`
- iptables:
  - `iptables -L -t nat | grep ...`
- Kube-proxy logs
  - `cat /var/log/kube-proxy.log`

- Using nslookup with Services:
  - `k exec -it pod-name -- nslookup nginx.default.cluster.local`