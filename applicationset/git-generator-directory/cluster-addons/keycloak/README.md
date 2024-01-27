# KEYCLOAK

## Setup Keycloak

## Keycloak Helm Chart

- [artifacthub.io, bitnami keycloak](https://artifacthub.io/packages/helm/bitnami/keycloak)

### Keycloak Operator Installation

Installing by using kubectl without Operator Lifecycle Manager



- [keycloak docs, operator installation](https://www.keycloak.org/operator/installation)
- [Artifacthub, keycloak operator](https://artifacthub.io/packages/olm/community-operators/keycloak-operator)

## Integrating Keycloak and ArgoCD

These instructions will take you through the entire process of getting your ArgoCD application authenticating with Keycloak. You will create a client within Keycloak and configure ArgoCD to use Keycloak for authentication, using groups set in Keycloak to determine privileges in Argo.

- [ArgoCD Operator manual, Integrating Keycloak and ArgoCD](https://argo-cd.readthedocs.io/en/stable/operator-manual/user-management/keycloak/)

## Resources

- [article medium, Integrate Keycloak and ArgoCD within Kubernetes with ease](https://medium.com/geekculture/integrate-keycloak-and-argocd-within-kubernetes-with-ease-6871c620d3b3)
- https://github.com/codecentric/helm-charts/tree/master
- https://artifacthub.io/packages/helm/bitnami/keycloak