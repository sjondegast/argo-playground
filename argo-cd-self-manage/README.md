# ArgoCD Self Managed

- [Medium Article, Self Managed Argo CD — App Of Everything](https://medium.com/devopsturkiye/self-managed-argo-cd-app-of-everything-a226eb100cf0)
- [GitHub repo, Self Managed Argo CD — App Of Everything](https://github.com/bukurt/argocd?source=post_page-----a226eb100cf0--------------------------------)

## Designing Git Repository Hierarchy

```sh
argocd/
├── argocd-appprojects      # stores ArgoCD App Project's yaml files
├── argocd-apps             # stores ArgoCD Application's yaml files
├── argocd-install          # stores Argo CD installation files
│ ├── argo-cd               # argo/argo-cd helm chart
│ └── values-override.yaml  # custom values.yaml for argo-cd chart
```
