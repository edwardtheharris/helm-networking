---
abstract: >-
   Helm Template documentation master file, created by
   sphinx-quickstart on Sun Apr 28 15:35:08 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
authors: Xander Harris
date: 2024-08-02
title: Calico Networking Helm Chart
---

## Repository Contents

```{contents}
```

```{toctree}
:caption: meta

.github/index
license
readme
security
```

## Indices and tables

* {ref}`genindex`
* {ref}`modindex`
* {ref}`search`

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
   also find [BGP Tools](https://bgp.tools) handy.
```

```{sectionauthor} Xander Harris <xandertheharris@gmail.com>
```
