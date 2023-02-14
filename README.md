# gitops

## Cluster addition
To add a new cluster to ArgoCD:
- Login with argocd CLI
```argocd login <argocd url>```
- Get the kubeconfig file of the "target" cluster, but don't 
```
kubectl karbon login --server <pc address> --insecure true --user <username>- -force true --kubeconfig ~/.kube/<cluster name>
export KUBECONFIG=~/.kube/<cluster name>
```
- Get the context of your cluster
```
kubectl config view
argocd cluster add <cluster name>-context
```

## Creat project and app
Copy / modify the two following manifest file defining the application and the project, and replace the values with the one corresponding to your setup, and apply them:
```
cp app-project-example.yaml app-project.yaml
cp app-of-app-example.yaml app-of-app.yaml
kubectl apply -f app-project.yaml
kubectl apply -f app-of-app.yaml
```

You should see the app-of-app created into your ArgoCD instance, and see the different appplications part of your app-of-app being deployed as well.