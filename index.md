---
abstract: >-
   Helm Template documentation master file, created by
   sphinx-quickstart on Sun Apr 28 15:35:08 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
authors:
   - name: Xander Harris
     email: xandertheharris@gmail.com
date: 2024-08-02
title: Calico Networking Helm Chart
---

## Repository Contents

```{contents}
```

### Dependencies

- [haproxy](https://artifacthub.io/packages/helm/haproxytech/haproxy)
- [kubernetes-ingress](https://artifacthub.io/packages/helm/haproxytech/kubernetes-ingress)

```{toctree}
:caption: contents

tests/index
```

```{toctree}
:caption: meta

.github/index
license
readme
security
```

## Indices and tables

- {ref}`genindex`
- {ref}`modindex`
- {ref}`search`

```{include} readme.md
```

### Chart

```{autoyaml} Chart.yaml
```

### Values

```{autoyaml} values.yaml
```

```{glossary}
BGP
   Border Gateway Protocol is a network routing protocol that operates at
   Layer 3 of the OSI model of the Internet. More information is available
   [here](https://en.wikipedia.org/wiki/Border_Gateway_Protocol). You may
   also find [BGP Tools](https://bgp.tools) handy. More information about
   Calico's BGP can be found
   [here](https://docs.tigera.io/calico/latest/networking/configuring/bgp).

calicoctl
   The calicoctl command line tool is required to use many of Calico's features.
   It is used to manage Calico policies and configuration, as well as view
   detailed cluster status. More information is available
   [here](https://docs.tigera.io/calico/latest/operations/calicoctl/install).

haproxy-ingress
   This is an ingress controller that deploys HAProxy to some or all of the
   nodes in a cluster and uses the in-cluster service to manage load balancing.
   More information is available
   [here](https://haproxy-ingress.github.io/). Note that this does not
   integrate with existing external HAProxy resources.

kubectl
   Kubernetes provides a command line tool for communicating with a Kubernetes
   cluster's control plane, using the Kubernetes API. More information is
   available [here](https://kubernetes.io/docs/reference/kubectl/).
```

```{sectionauthor} Xander Harris <xandertheharris@gmail.com>
```
