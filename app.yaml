apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: intern
  namespace: argocd
  # annotations:
  #   argocd-image-updater.argoproj.io/image-list: 548844171305.dkr.ecr.us-east-1.amazonaws.com/private-example:~v0.4
    #argocd-image-updater.argoproj.io/app-version.pull-secret: secret:argocd/aws-ecr-creds#creds
    # argocd-image-updater.argoproj.io/write-back-method: git
  finalizers:
    - resources-finalizer.argocd.argoproj.io
spec:
  destination:
    namespace: default
    server: 'https://kubernetes.default.svc'
  source:
    path: Chart-test/
    repoURL: 'https://github.com/Khachik001/helm.git'
    targetRevision: HEAD
    helm:
      valueFiles:
        - values.yaml
  project: default
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
      allowEmpty: false
    syncOptions:
      - Validate=true
      - CreateNamespace=true
      - PrunePropagationPolicy=foreground
      - PruneLast=true
