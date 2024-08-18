#### Logs and Monitoring

- Metrics Server
  - Nodes Metrics:
    - `kubectl top nodes`
  - PODs Metrics:
    - `kubectl top pods -n default`
    - `kubectl top pods -A`
- Logs
  - `kubectl logs mypod`
  - `kubectl logs mypod containername`