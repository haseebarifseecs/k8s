# Restricting Access by binding role to a ServiceAccount in default namespace.

#### Apply manifests using 
```
kubectl apply -f ./RBAC
```

#### Obtain the Token from the Secret

```
kubectl get secrets "SecretName" -o yaml
```

#### Decode the secret

```
echo "Base64 Encoded Secret" | base64 --decode
```

#### Create a new Context

```
kubectl config set-context "ContextName" --cluster "ClusterName" --user "SA"
```

#### Once Context is Created Add token to the user

```
kubectl set-credentials "user" --token "TOKEN VALUE"
```

#### Use the context

```
kubectl config use-context "ContextName"

```

### Link the User

```
kubectl config set-context --current --user "SA"
```

### You can also verify the context, cluster and the associated token by looking at the contents of kubeconfig
```
cat ~/.kube/config
```
### Verify the RBAC

```
kubectl auth can-i get pods --> YES
kubectl auth can-i create deployments --> NO
```



