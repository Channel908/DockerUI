# DockerK8SUI

## Create a Service Account

We are creating Service Account with the name `admin-user` in namespace `kubernetes-dashboard` first.

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user
  namespace: kubernetes-dashboard
```
