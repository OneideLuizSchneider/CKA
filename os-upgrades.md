#### OS Upgrades / maintenance / etc

To be able to reboot, make changes/upgrades on the OS without have downtime you can use the commands bellow:

- `kubectl drain nodename`
  - Recreates all the PODs in other Nodes and mark the Node as unscheduled, but keep in mind that if you don't have more replicas your service have some downtime.
- `kubectl cordon nodename`
  - Mark the Node as unscheduled
- `kubectl uncordon nodename`
  - It will make the Node schedulable again.

- To ignore daemonsets, just add:
  - `--ignore-daemonsets`