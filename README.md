# Docker Desktop Kubernetes with UI

## Create a Service Account

Creating a Service Account with the name `admin-user` in namespace `kubernetes-dashboard` first.

dockerui-user-account.yaml
```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user
  namespace: kubernetes-dashboard
```
