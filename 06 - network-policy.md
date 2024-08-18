#### Network Policy

- If you want to control traffic flow at the IP address or port level for TCP, UDP, and SCTP protocols, then you might consider using Kubernetes NetworkPolicies for particular applications in your cluster.


Egress Example:
```
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: internal-policy
  namespace: default
spec:
  podSelector:
    matchLabels:
      name: internal
  egress:
  - to:
    - podSelector:
        matchLabels:
          name: service1
    ports:
    - port: 8080
      protocol: TCP

  - to:
    - podSelector:
        matchLabels:
          name: db-mysql

    ports:
    - port: 3306
      protocol: TCP

  policyTypes:
  - Egress
```

This will allow only egress traffic to `service1` and `db-mysql` and to ports `8080`,`3306` 


Ingress example:
```
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: my-network-policy
  namespace: default
spec:
  podSelector:
    matchLabels:
      role: db

  policyTypes:
  - Ingress

  ingress:
  - from:
    - podSelector:
        matchLabels:
          role: api
    ports:
    - protocol: TCP
      port: 3306
```
This will allow traffic to the label `db` from the label `api`, and to port `3306`

