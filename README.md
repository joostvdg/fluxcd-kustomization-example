# TMC and FluxCD

## Source

```yaml
---
apiVersion: source.toolkit.fluxcd.io/v1beta2
kind: GitRepository
metadata:
  name: $REPO_NAME
  namespace: flux-system
spec:
  interval: 30s
  ref:
    branch: master
  url: $REPO_URL

```

## Kustomization

```yaml
---
apiVersion: kustomize.toolkit.fluxcd.io/v1beta2
kind: Kustomization
metadata:
  name: $REPO_NAME
  namespace: flux-system
spec:
  interval: 5m0s
  path: ./kustomizations
  prune: true
  sourceRef:
    kind: GitRepository
    name: $REPO_NAME
  targetNamespace: default
```