---
abstract: >-
    A Helm Chart to install various Calico networking resources to a K8S
    cluster.
authors:
    - name: Xander Harris
      email: xandertheharris@gmail.com
date: 2024-04-02
title: Readme
---

[![CodeQL](https://github.com/edwardtheharris/helm-calico/actions/workflows/codeql.yml/badge.svg)](https://github.com/edwardtheharris/helm-calico/actions/workflows/codeql.yml)
[![Documentation](https://github.com/edwardtheharris/helm-calico/actions/workflows/documentation.yml/badge.svg)](https://github.com/edwardtheharris/helm-calico/actions/workflows/documentation.yml)
[![OSSAR](https://github.com/edwardtheharris/helm-calico/actions/workflows/ossar.yml/badge.svg)](https://github.com/edwardtheharris/helm-calico/actions/workflows/ossar.yml)
[![Test Helm Chart](https://github.com/edwardtheharris/helm-calico/actions/workflows/helm.yml/badge.svg)](https://github.com/edwardtheharris/helm-calico/actions/workflows/helm.yml)
[![wakatime](https://wakatime.com/badge/github/edwardtheharris/helm-calico.svg)](https://wakatime.com/badge/github/edwardtheharris/helm-calico)

This chart deploys Calico networking resources to an existing K8S cluster.

## Usage

Before using this chart, you will probably want to be familiar with the
concepts described the
[quick start guide](https://docs.tigera.io/calico/latest/getting-started/kubernetes/self-managed-onprem/onpremises).

### Install

To install this chart follow these steps.

1. Install the {term}`calicoctl` executable.

   ```shell
   cd /usr/local/bin/
   curl -L https://github.com/projectcalico/calico/releases/download/v3.28.1/calicoctl-linux-amd64 \
      -o calicoctl
   sudo chmod +x calicoctl
   ```

2. Install the {term}`kubectl` plugin for {term}`calicoctl`.

   ```shell
   cd /usr/local/bin
   curl -L https://github.com/projectcalico/calico/releases/download/v3.28.1/calicoctl-linux-amd64 \
      -o kubectl-calico
   sudo chmod +x kubectl-calico
   ```

3. Create a namespace for Calico.

   ```shell
   kubectl create ns calico-system
   ```

4. Sort out the best choice for your network.

   You can find information on how to do that
   [here](https://docs.tigera.io/calico/latest/networking/determine-best-networking).
5. Adjust the contents of {file}`values.yaml` for your network.
6. Install the chart.

   ```shell
   helm -n calico-system install calico .
   ```

7. Continue with configuring your clusters networking.

### Uninstall

This can be done in the usual way.

```shell
helm -n calico-system uninstall calico
```
