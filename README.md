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

## Create a ClusterRoleBinding

dockerui-cluster-role.yaml
```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: admin-user
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
- kind: ServiceAccount
  name: admin-user
  namespace: kubernetes-dashboard
```
