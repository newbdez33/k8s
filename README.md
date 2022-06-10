# K8S local

## Refers

<https://8gwifi.org/docs/kube-nginx.jsp/>
<https://kubernetes.io/zh/docs/tutorials/configuration/configure-redis-using-configmap/>

## Port fowarding

```shell
kubectl port-forward deployment/mysql 3306:3306
kubetl port-forward pods/redis 6379:6379
```

## Nginx self-signed reverse proxy

```shell
kubectl create secret generic nginx-certs-keys --from-file=./nginx/nginx.crt --from-file=./nginx/nginx.key --from-file=./nginx/dhparam.pem
kubectl create configmap nginx-config --from-file=./nginx/default.conf
//update config
kubectl create configmap nginx-config --from-file=./nginx/default.conf -o yaml --dry-run=client | kubectl apply -f -
kubectl apply -f nginx-app.yaml
```
