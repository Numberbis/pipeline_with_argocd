# pipeline_with_argocd

Ce dépôt fournit un exemple minimal de pipeline CI/CD utilisant **Argo CD** pour déployer un simple blog statique sur le thème DevOps.

## Structure du projet

- `blog/` : contient les pages HTML du blog DevOps.
- `Dockerfile` : image basée sur Nginx servant les fichiers statiques.
- `k8s/` : manifests Kubernetes (Deployment et Service).
- `argocd/application.yaml` : définition de l'application Argo CD.
- `.github/workflows/ci-cd.yml` : pipeline GitHub Actions de build et de déploiement.

## Utilisation

1. Poussez ce dépôt sur GitHub.
2. Configurez les secrets `ARGOCD_SERVER`, `ARGOCD_USERNAME` et `ARGOCD_PASSWORD` dans votre repository GitHub pour permettre à la pipeline de déclencher Argo CD.
3. Adaptez dans `k8s/deployment.yaml` l'image container `ghcr.io/USERNAME/pipeline_blog:latest` avec votre nom d'utilisateur.
4. Installez Argo CD sur votre cluster Kubernetes puis appliquez `argocd/application.yaml`.
5. À chaque `git push` sur la branche `main`, le workflow construit l'image, la pousse sur GHCR puis synchronise l'application via Argo CD.
