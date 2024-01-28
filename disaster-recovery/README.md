# README.md

You can use `argocd admin` to import and export all Argo CD data.

Make sure you have `~/.kube/config` pointing to your Argo CD cluster.

## Figure out what version of Argo CD you're running:

```sh
# argocd version | grep server
argocd version
export VERSION=v2.9.3

```

## Export to a backup

```sh
# Export to a backup:
docker run -v ~/.kube:/home/argocd/.kube --rm quay.io/argoproj/argocd:$VERSION argocd admin export > backup.yaml
```

## Import from a backup:

```sh
docker run -i -v ~/.kube:/home/argocd/.kube --rm quay.io/argoproj/argocd:$VERSION argocd admin import - < backup.yaml
```

## Resources

- [argoCD docs Disaster Recovery](https://argo-cd.readthedocs.io/en/stable/operator-manual/disaster_recovery/)