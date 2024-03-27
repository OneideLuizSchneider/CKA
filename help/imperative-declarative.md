#### Imperative

Examples:
> kubectl run --image=nginx nginx
> kubectl create deployment --image=nginx nginx
> kubectl expose deployment nginx --port 80
> kubectl scale deployment nginx --replicas=5

#### Declarative

Examples:
> kubectl apply –f nginx.yaml
> kubectl delete –f nginx.yaml