---
abstract: Continuous Integration, Deployment, and Delivery usage.
authors: Xander Harris
date: 2024-04-28
title: CI/CD usage guide
---

Or something like it.

## GitHub Actions Workflows

This repository uses the following GitHub Actions Workflows.

### CodeQL Workflow

[![CodeQL](https://github.com/edwardtheharris/helm-calico/actions/workflows/codeql.yml/badge.svg)](https://github.com/edwardtheharris/helm-calico/actions/workflows/codeql.yml)

```{autoyaml} .github/workflows/codeql.yml
```

### Documentation Workflow

[![Documentation](https://github.com/edwardtheharris/helm-calico/actions/workflows/documentation.yml/badge.svg)](https://github.com/edwardtheharris/helm-calico/actions/workflows/documentation.yml)

```{autoyaml} .github/workflows/documentation.yml
```

### Helm Workflow

[![Test Helm Chart](https://github.com/edwardtheharris/helm-calico/actions/workflows/helm.yml/badge.svg)](https://github.com/edwardtheharris/helm-calico/actions/workflows/helm.yml)

```{autoyaml} .github/workflows/helm.yml
```

### OSSAR Workflow

[![OSSAR](https://github.com/edwardtheharris/helm-calico/actions/workflows/ossar.yml/badge.svg)](https://github.com/edwardtheharris/helm-calico/actions/workflows/ossar.yml)

```{autoyaml} .github/workflows/ossar.yml
```

## Dependabot Settings

```{autoyaml} .github/dependabot.yml
```
