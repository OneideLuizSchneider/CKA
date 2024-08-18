#### kube-scheduler

- You can add as many kube-schedulers as you need.

```
apiVersion: v1
kind: Pod
metadata:
  name: my-custom-scheduler
  namespace: kube-system
spec:
  containers:
  - command:
    - kube-scheduler
    - --address=127.0.0.1
    - --kubeconfig=/etc/kubernetes/scheduler.conf
    - --leader-elect=true
    image: k8s.gcr.io/kube-scheduler-amd64:v1.11.3
    name: kube-scheduler
    - --scheduler-name=my-custom-scheduler
    - --lock-object-name=my-custom-scheduler
```

How to use it(`schedulerName`):
```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  namespace: default
  labels:
    app: nginx
spec:
  containers:
  - name: nginx
    image: nginx:latest

  schedulerName: my-custom-scheduler  

```

#### Scheduler Process

- The user starts a new pod.

- **Scheduler Queue**: This is the QueueSort phase. Pod is added to the scheduling queue. Based on the priority given to the pod it starts to schedule the pod PriorityClasses.

- **Filtering**: This is the Filter phase. In this phase nodes that cannot schedule the pod are filtered based on resource limits, taints & tolerations, etc.

- **Scoring**: This is the Score phase. In this phase, the scheduler scores the nodes filtered based on the free space available before and after scheduling and then assigns a score. The node with the highest score is taken.

- **Binding**: This is the Bind phase. In this phase, the pod is bound to the node with the highest score and now the pod is finally scheduled.



Official doc: 
- <https://kubernetes.io/docs/tasks/extend-kubernetes/configure-multiple-schedulers/>
- <https://kubernetes.io/docs/concepts/scheduling-eviction/>