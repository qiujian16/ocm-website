---
title: Install Application management
weight: 3
---

After hub is installed, you could install the application management components to the hub.

<!-- spellchecker-disable -->

{{< toc >}}

<!-- spellchecker-enable -->

## Install from source
Clone the `multicloud-operators-subscription`

```Shell
git clone https://github.com/open-cluster-management/multicloud-operators-subscription
```

Deploy a stand-alone subscription operator

```Shell
cd multicloud-operators-subscription
kubectl apply -f deploy/standalone
```

## Install from OperatorHub
If you are using Openshift or have `OLM` installed in your cluster, you are able to install the multicluster subscription operator with a released version from operartorhub. Details can be found [here](https://operatorhub.io/operator/multicluster-operators-subscription)

## What is next

After a successfull deployment, test the subscription operator with a `helm` subscription

```Shell
kubectl apply -f examples/helmrepo-channel
kubectl patch subscriptions.apps.open-cluster-management.io simple --type='json' -p='[{"op": "replace", "path": "/spec/placement/local", "value": true}]'
kubectl get appsub/simple -o yaml

```
