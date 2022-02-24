# argocd

ArgoCD deployment for my local test setup

## Perquisites 

Install Helm/Kind/Git/k9s/kubectl

```bash
brew install helm
brew install kind
git clone https://github.com/whume/argocd.git
```

## Usage

```bash
# Create a kind cluster 
cd argocd/
kind create cluster --config cluster-configs/kind-config.yaml

# Install Argocd 
cd argocd-install/
helm install argocd ./argo-cd --namespace=argocd --create-namespace -f values-override.yaml

```
Access ArgoCD on localhost port 80

[localhost](http:localhost)

Get ArgoCD admin password
```bash
kubectl -n argocd get secrets argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d
```

## Apps Installed
+ Self Managed ArgoCD 
+ Nginx Ingress on port 80 and 443 of localhost
+ Kube-Prometheus

## License
[MIT](https://choosealicense.com/licenses/mit/)