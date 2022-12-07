# Accessing API Server using CURL
#### By default API Server is listening on Port 6443 and uses TLSv1.3 by using self signed CACert and Client Certs and Keys.
#### Certificate information is present in the kubeconfig file located at the 
```
$HOME/.kube/config or ~/.kube/config
```
#### **kubectl** uses the kubeconfig file to authenticate and authorize with the server. 

#### We can CURL and parse the certificates to accecss the APIEndpoint over HTTPS.
#### First we need to extract the certs from the kubeconfig.

```
cat ~/.kube/config | yq .clusters[0].cluster.certificate-authority-data | base64 -d -
cat ~/.kube/config | yq .users[0].user.client-certificate-data | base64 -d -
cat ~/.kube/config | yq .users[0].user.client-key-data | base64 -d -
```

#### We can also save the output to a file.

```
cat ~/.kube/config | yq .clusters[0].cluster.certificate-authority-data | base64 -d - > ca.crt
```

#### Once we have all the certificates we can use them to query the apiserver.

```
curl -vvv -k https://127.0.0.1:6443/api/v1/pods --cacert ca.crt --cert client.crt --key client.key
```

