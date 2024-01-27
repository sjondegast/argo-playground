# README

- https://cert-manager.io/docs/installation/helm/
- https://cert-manager.io/docs/installation/best-practice/
- https://cert-manager.io/docs/installation/operator-lifecycle-manager/
- [ ] using operator, Operator Lifecycle manager?
- Chart.yaml

```yaml
apiVersion: v2
name: example_chart
description: A Helm chart with cert-manager as subchart
type: application
version: 0.1.0
appVersion: "0.1.0"
dependencies:
  - name: cert-manager
    version: v1.13.3
    repository: https://charts.jetstack.io
    alias: cert-manager
    condition: cert-manager.enabled
```
