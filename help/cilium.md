#### Cilium

Helm Install:
```
helm repo add cilium https://helm.cilium.io/

helm install cilium cilium/cilium \
  --version 1.16.0 \
  --namespace kube-system
```

Restart Pods:
```
kubectl get pods --all-namespaces -o custom-columns=NAMESPACE:.metadata.namespace,NAME:.metadata.name,HOSTNETWORK:.spec.hostNetwork --no-headers=true | grep '<none>' | awk '{print "-n "$1" "$2}' | xargs -L 1 -r kubectl delete pod
```

Test installation:
```
kubectl create ns cilium-test
kubectl get pods -n cilium-test

kubectl get pods -n cilium-test
```

Once done with the test, remove the cilium-test namespace:
```
kubectl delete ns cilium-test
```

Doc:
- <https://docs.cilium.io/en/stable/>