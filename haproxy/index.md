---
abstract: >-
   This folder contains configuration related to setting up HAProxy for use
   as an external LB for Kubernetes.
authors:
   - name: Xander Harris
     email: xandertheharris@gmail.com
date: 2024-09-02
title: HAProxy
---

```{note}
The information outlined here is sourced from
[this](https://www.haproxy.com/documentation/kubernetes-ingress/community/installation/external-mode-on-premises/#install-the-ingress-controller-outside-of-your-cluster)
document.
```

To enable this functionality follow this process.

1. Stop and disable any running haproxy service.

   ```{code-block} shell
   systemctl stop haproxy
   systemctl disable haproxy
   ```

2. Update the system capabilities of the haproxy executable.

   ```{code-block} shell
   setcap cap_net_bind_service=+ep /usr/sbin/haproxy
   ```

3. Download, unzip, and set the executable bit on the ingress controller.

   ```{code-block} shell
   wget https://github.com/haproxytech/kubernetes-ingress/releases/download/v1.8.8/haproxy-ingress-controller_1.8.8_Linux_x86_64.tar.gz
   tar -xzvf haproxy-ingress-controller_1.8.8_Linux_x86_64.tar.gz
   cp ./haproxy-ingress-controller /usr/local/bin/
   ```

4. Replace the haproxy systemd service with the config here.

   ```{literalinclude} /haproxy/haproxy.service
   :language: systemd
   ```

5. Restart and re-enable the haproxy service.

   ```{code-block} shell
   systemctl enable haproxy
   systemctl start haproxy
   ```

6. Install the BiRD routing service.

   ```{code-block} shell
   pacman -Syu bird
   ```

7. Configure the service using the file in this folder by copying it to the
   load balancer at `/etc/bird/bird.conf`.

   ```{literalinclude} /haproxy/bird.conf
   ```

8. Enable and start the BiRD routing service

   ```{code-block} shell
   systemctl enable bird
   systemctl restart bird
   ```

9. Use the example deployment and service here to see that it works.

   ```{code-block} shell
   kubectl apply -f haproxy/example-deployment.yaml
   kubectl apply -f haproxy/example-ingress.yaml
   ``

Additional information is available [here](https://www.haproxy.com/documentation/kubernetes-ingress/ingress-tutorials/routing/).
