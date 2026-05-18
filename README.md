# Reusable Shared GitHub Automation

Shared GitHub automation for two reuse patterns:

- composite actions under `.github/actions/`
- reusable workflows under `.github/workflows/`

Use composite actions when the calling repository should keep control of the job and compose its own steps. Use reusable workflows when the calling repository should delegate an entire job through `workflow_call`.

## Repository layout

```text
.github/
  actions/
    checkov/
    docker-build-push/
    gitleaks/
    node-ci/
    trivy/
    update-k8s-image-tag/
  workflows/
    checkov.yml
    docker-build-push.yml
    gitleaks.yml
    node-ci.yml
    sonarcloud.yml
    trivy.yml
```

## Composite actions

See [.github/actions/README.md](./.github/actions/README.md).

Current actions:

- `argocd-sync`
- `gitleaks`
- `node-ci`
- `notification`
- `checkov`
- `trivy`
- `docker-build-push`
- `update-k8s-image-tag`

## Reusable workflows

See [.github/workflows/README.md](./.github/workflows/README.md).

Current workflows:

- `gitleaks.yml`
- `checkov.yml`
- `trivy.yml`
- `sonarcloud.yml`
- `node-ci.yml`
- `docker-build-push.yml`

## Usage guidance

Choose composite actions when:

- you want multiple repos to share step logic
- you want each pipeline to keep its own job names, sequencing, and conditions
- you want a showcase of reusable action composition

Choose reusable workflows when:

- you want a standard job contract reused across repositories
- you want to centralize an entire stage behind `uses: owner/repo/.github/workflows/file.yml@ref`

## Notes

- Push this repository before pushing dependent repositories that consume these actions by branch or tag.
- For private cross-repo updates such as Kubernetes manifest commits, provide a token with the required repository permissions.
