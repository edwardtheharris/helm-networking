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

## Calico

The recommended method for installing Calico for networking is with the
[Tigera Operator](https://docs.tigera.io/calico/latest/getting-started/kubernetes/self-managed-onprem/onpremises).

1. Install the operator.

   ```{code-block} shell
   kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.28.2/manifests/tigera-operator.yaml
   ```

   Success looks like this.

   ```{code-block} shell
   namespace/tigera-operator created
   customresourcedefinition.apiextensions.k8s.io/bgpconfigurations.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/bgpfilters.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/bgppeers.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/blockaffinities.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/caliconodestatuses.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/clusterinformations.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/felixconfigurations.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/globalnetworkpolicies.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/globalnetworksets.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/hostendpoints.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/ipamblocks.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/ipamconfigs.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/ipamhandles.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/ippools.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/ipreservations.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/kubecontrollersconfigurations.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/networkpolicies.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/networksets.crd.projectcalico.org created
   customresourcedefinition.apiextensions.k8s.io/apiservers.operator.tigera.io created
   customresourcedefinition.apiextensions.k8s.io/imagesets.operator.tigera.io created
   customresourcedefinition.apiextensions.k8s.io/installations.operator.tigera.io created
   customresourcedefinition.apiextensions.k8s.io/tigerastatuses.operator.tigera.io created
   serviceaccount/tigera-operator created
   clusterrole.rbac.authorization.k8s.io/tigera-operator created
   clusterrolebinding.rbac.authorization.k8s.io/tigera-operator created
   deployment.apps/tigera-operator created
   ```

2. Download custom resources.

   ```{code-block} shell
   curl https://raw.githubusercontent.com/projectcalico/calico/v3.28.2/manifests/custom-resources.yaml -O
   ```

3. Install custom resources.

   ```{code-block} shell
   kubectl create -f custom-resources.yaml
   ```
