# ArgoCD Notes

- Argo CD cli but Argo CD cli does not deploy an opinionated GitOps setup.
- It solves different problems then flux does.
- Those who are familiar with Flux can easily imagine what a bootstrapper cli is and how that is helpful since Flux uses Flux bootstrap cli to deploy an opinionated GitOps setup.
- Argo CD autopilot is a cli tool to bootstrap self managed Argo CD on a Kubernetes cluster and creates a Git repository as the single source of truth.

When you bootstrap your Argo CD setup with autopilot you get a structured private git repository, opinionated folders to put your own application resources and logical grouping of applications named projects, self managed Argo CD controllers including ApplicationSet controller and a secret to pull desired state from git repository.
