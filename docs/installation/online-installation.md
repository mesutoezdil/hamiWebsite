---
sidebar_label: Online Installation from Helm
title: Online Installation from Helm (Recommended)
---

The recommended way to deploy HAMi is via Helm.

## Add HAMi repo

You can add HAMi chart repository using the following command:

```bash
helm repo add hami-charts https://project-hami.github.io/HAMi/
helm repo update
```

## Check your Kubernetes version

A Kubernetes version is required for a successful installation. You can retrieve your Kubernetes server version with:

```bash
kubectl version
```

## Installation

Ensure the `scheduler.kubeScheduler.image.tag` matches your Kubernetes server version. For instance, if your cluster server is running Kubernetes v1.29.0, use the following command to deploy:

```bash
helm install hami hami-charts/hami --set scheduler.kubeScheduler.image.tag=v1.29.0 -n kube-system
```

Customize your installation by editing the [configurations](../userguide/configure.md).

## Verify your installation

You can verify your installation using the following command:

```bash
kubectl get pods -n kube-system
```

If both the hami-device-plugin and hami-scheduler pods are `Running` and `Ready`, your installation is successful.
