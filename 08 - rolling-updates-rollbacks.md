##### Rolling Updates & Rollbacks

- Rolling Update is the default strategy in k8s.
  - IF you describe a deployment you'll see:
    - `StrategyType: RollingUpdate`

- Rollout Command: 
  ```
  kubectl set image deployment/myapp nginx=nginx:1.10

  kubectl rollout status deployment/myapp
  
  kubectl rollout history deployment/myapp  
  ```

- Rollback:
  `kubectl rollout undo deployment/myapp`
