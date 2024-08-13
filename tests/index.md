---
abstract: >-
    This is the index for the Helm unit tests for the Calico chart.
authors:
    - name: Xander Harris
      email: xandertheharris@gmail.com
date: 2024-08-02
title: Calico Networking Unit Tests
---

## Run the tests

1. Install the [helm-unittest](https://github.com/helm-unittest/helm-unittest)
   plugin.

   ```{code-block} shell
   helm plugin install https://github.com/helm-unittest/helm-unittest
   ```

2. Run the tests.

   ```{code-block} shell
   helm unittest -f 'tests/*.yaml' .
   ```

   If things went well, you should see something similar to this.

   ```{code-block} shell
   ### Chart [ calico ] .

    PASS  test suite for BGPPeer   tests/bgppeer_test.yaml
    PASS  test suite for Calico Node Status object tests/caliconodestatus_test.yaml
    PASS  test suite for IPPool    tests/ippool_test.yaml

   Charts:      1 passed, 1 total
   Test Suites: 3 passed, 3 total
   Tests:       3 passed, 3 total
   Snapshot:    0 passed, 0 total
   Time:        9.980651ms
   ```

## Included tests

The following test suites are run from this repository.

### BGPPeer test

```{autoyaml} tests/bgppeer_test.yaml
```

### Calico Node Status test

```{autoyaml} tests/caliconodestatus_test.yaml
```

### IPPool test

```{autoyaml} tests/ippool_test.yaml
```
