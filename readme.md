---
abstract: >-
    A Helm Chart to install various Calico networking resources to a K8S
    cluster.
authors:
    - name: Xander Harris
      email: xandertheharris@gmail.com
date: 2024-04-02
title: Calico Network Helm Chart
---

This chart deploys Calico networking resources to an existing K8S cluster.

## Usage

Before using this chart, you will probably want to be familiar with the
concepts described the
[quick start guide](https://docs.tigera.io/calico/latest/getting-started/kubernetes/self-managed-onprem/onpremises).

### Install

To install this chart follow these steps.

```shell
helm install calico .
```

### Uninstall

This can be done in the usual way.

```shell
helm uninstall uninstall calico
```
