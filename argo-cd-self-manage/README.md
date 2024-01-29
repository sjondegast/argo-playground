# Manage Argo CD Using Argo CD

Argo CD is able to manage itself since all settings are represented by Kubernetes manifests. The suggested way is to create [Kustomize](https://github.com/kubernetes-sigs/kustomize) based application which uses base Argo CD manifests from https://github.com/argoproj/argo-cd and apply required changes on top.

Example of `kustomization.yaml`:

```yaml
# additional resources like ingress rules, cluster and repository secrets.
resources:
- github.com/argoproj/argo-cd//manifests/cluster-install?ref=v1.0.1
- clusters-secrets.yaml
- repos-secrets.yaml

# changes to config maps
patches:
- path: overlays/argo-cd-cm.yaml
```

The live example of self managed Argo CD config is available at https://cd.apps.argoproj.io/ and with configuration stored at [argoproj/argoproj-deployments](https://github.com/argoproj/argoproj-deployments/tree/master/argocd).

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
