# mypoc-argo

## Steps

### Configure kubeconfig 
`export KUBECONFIG=/Users/polyogitag/myprojects/myhelmchart-argo/mypoc-cluster-kubeconfig.yaml`

### Configure namespace for Argocd
`kubectl apply -f 0-namespaces.yml`
### Install Argocd

`kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
`
### Now do port forwarding to check Argocd UI
- To get the port details use below command

`kubectl get svc -n argocd`

- To do port foword use below command

`kubectl port-forward -n argocd svc/argocd-server 8080:443`

- To access Argocd UI use below link in browser

`https://localhost:8080`

### To get the secret for password of Argocd GUI

`argoPass=$(kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d)`

`echo $argoPass`


