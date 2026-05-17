# Composite Actions

This directory contains reusable composite actions intended to be checked out by another repository and invoked through a local path such as:

```yaml
- uses: actions/checkout@v4
  with:
    repository: marjorieechu/reusable-shared-gh-workflows
    ref: main
    path: ./.reusable-actions

- uses: ./.reusable-actions/.github/actions/node-ci
```

## Available actions

- `gitleaks`: secret scanning
- `node-ci`: Node.js install, test, and build
- `checkov`: IaC scanning
- `trivy`: filesystem, config, or image vulnerability scanning
- `docker-build-push`: Docker build and optional push
- `update-k8s-image-tag`: cross-repo Kubernetes manifest image update
