# restful-app-k8s

k8s base environment of [restful-app](https://github.com/tuananhhedspibk/restful-app)

For local environment, you must install argocd for raising up and then executing the following commands to start up:

1. To get argocd password

```sh
$kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

2. Login into argocd

```sh
$argocd login localhost:8080 --username admin --password <password>
```

3. Create app

```sh
$argocd app create restful-app \
--repo https://github.com/tuananhhedspibk/restful-app-k8s \
--path overlays/dev \
--dest-server https://kubernetes.default.svc \
--dest-namespace default
```

4. Sync the newest state of app

```sh
$argocd app sync restful-app
```
