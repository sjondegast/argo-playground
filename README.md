# argo-playground

All resources, including Application and AppProject specs, have to be installed in the Argo CD namespace (by default argocd).

- https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#atomic-configuration
- https://argo-cd.readthedocs.io/en/stable/operator-manual/argocd-repositories-yaml/
- https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/
- https://argo-cd.readthedocs.io/en/stable/operator-manual/project-specification/

## ArgoCD Setup

- argoCD config
- https://github.com/argoproj/argo-cd/blob/2d6ce088acd4fb29271ffb6f6023dbb27594d59b/docs/operator-manual/argocd-cm.yaml#L279-L282

## Declarative Setup

!this chaptor should be its own wiki

### Applications

#### [App of Apps](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#app-of-apps)

You can create an app that creates other apps, which in turn can create other apps.
This allows you to declaratively manage a group of apps that can be deployed and configured in concert.

#### [Cluster Bootstrapping](https://argo-cd.readthedocs.io/en/stable/operator-manual/cluster-bootstrapping/#cluster-bootstrapping)

This guide is for operators who have already installed Argo CD, and have a new cluster and are looking to install many apps in that cluster.

There's no one particular pattern to solve this problem, e.g. you could write a script to create your apps, or you could even manually create them. However, users of Argo CD tend to use the app of apps pattern.

### [Projects](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#projects)

### [Repositories](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#repositories)

#### [Manage Argo CD Using Argo CD](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#manage-argo-cd-using-argo-cd)

Argo CD is able to manage itself since all settings are represented by Kubernetes manifests. 
The suggested way is to create [Kustomize](https://github.com/kubernetes-sigs/kustomize) based application which uses base Argo CD manifests,
from [https://github.com/argoproj/argo-cd](https://github.com/argoproj/argo-cd) and apply required changes on top.

Example of kustomization.yaml:

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

The live example of self managed Argo CD config is available at [https://cd.apps.argoproj.io](https://cd.apps.argoproj.io/) and with configuration stored at [argoproj/argoproj-deployments](https://github.com/argoproj/argoproj-deployments/tree/master/argocd).

## [Secret Management](https://argo-cd.readthedocs.io/en/stable/operator-manual/secret-management/#secret-management)

Argo CD is un-opinionated about how secrets are managed. There are many ways to do it, and there's no one-size-fits-all solution.

Many solutions use plugins to inject secrets into the application manifests. See Mitigating Risks of Secret-Injection Plugins below to make sure you use those plugins securely.

Here are some ways people are doing GitOps secrets:

- [Bitnami Sealed Secrets](https://github.com/bitnami-labs/sealed-secrets)
- [Helm Secrets](https://github.com/jkroepke/helm-secrets)
- [Kustomize secret generator plugins](https://github.com/kubernetes-sigs/kustomize/blob/fd7a353df6cece4629b8e8ad56b71e30636f38fc/examples/kvSourceGoPlugin.md#secret-values-from-anywhere)
- [Hashicorp Vault](https://www.vaultproject.io/)

## ArgoCD Features

- [Config Management Plugins](https://argo-cd.readthedocs.io/en/stable/operator-manual/config-management-plugins/#config-management-plugins)