# Docker Desktop Kubernetes with UI

## Install the Docker Kubernetes UI

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
```
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

```
kubectl apply -f dockerui-user-account.yaml
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
```
kubectl apply -f dockerui-cluster-role.yaml
```

## Get the Service Account Security Token

```
kubectl -n kubernetes-dashboard create token admin-user
```

## Start the Proxy

```
kubectl proxy
```

## Launch the Dashboard

```
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
```
