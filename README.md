# OpenShift Virtualization meets GitOps

This repo provides examples on how to deploy VMs in OpenShift Virtualization using a GitOps approach.

The following YAML defines the Argo CD Application:

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: 'APPLICATION NAME'
spec:
  destination:
    namespace: 'NAMESPACE'
    server: https://kubernetes.default.svc
  source:
    path: 'PATH'
    repoURL: https://github.com/rguske/gitops-vms/
    targetRevision: HEAD
  project: default
  syncPolicy:
    automated:
      prune: false
      selfHeal: true
    syncOptions:
      - CreateNamespace=true
```

![example-image](static/image1.png)