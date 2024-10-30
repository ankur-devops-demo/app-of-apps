apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: sock-shop
  namespace: argocd
spec:
  project: default
  source:
    repoURL: https://github.com/ankur-devops-demo/argocd-example-apps
    path: sock-shop
    targetRevision: hook-sync-demo
  destination:
    server: https://kubernetes.default.svc
    namespace: sock-shop
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
    syncOptions:
      - CreateNamespace=true