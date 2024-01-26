# NOTES

## Issue helm chart version and dependencies not resolving

```
Failed to load target state: failed to generate manifest for source 1 of 1: rpc error: code = Unknown desc = Manifest generation error (cached): `helm dependency build` failed exit status 1: load.go:120: Warning: Dependencies are handled in Chart.yaml since apiVersion "v2". We recommend migrating dependencies to Chart.yaml. load.go:120: Warning: Dependencies are handled in Chart.yaml since apiVersion "v2". We recommend migrating dependencies to Chart.yaml. Error: can't get a valid version for repositories keycloak. Try changing the version constraint in Chart.yaml
```