---
layout: post
title: Kubernets with docker-for-desktop on Mac
category: technology

---

If you are looking to get your dev setup to use Dockers and run on Kubernetes then Docker have a much simpler option and in fact ready to use Kubernetes option if you are on **Mac 18.06.0-ce-mac70 CE and higher**. Simply enable Kubernetes from the Docker desktop menu.

And if you want Kubernetes to be your default stack for deployment then you can enable it as below;



Assuming you have Kubectl installed separately, then you will be able to confirm that the Kubernetes cluster is setup by running the following;

```bash
$ kubectl config current-context
docker-for-desktop
```

If you want to check full info;

```bash
$ kubectl cluster-info
Kubernetes master is running at https://localhost:6443
Heapster is running at https://localhost:6443/api/v1/namespaces/kube-system/services/heapster/proxy
KubeDNS is running at https://localhost:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
monitoring-influxdb is running at https://localhost:6443/api/v1/namespaces/kube-system/services/monitoring-influxdb/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

And to check nodes in the cluster

```bash
$ kubectl get nodes
NAME                 STATUS   ROLES    AGE   VERSION
docker-for-desktop   Ready    master   4d    v1.10.11
```



**Kubernetes Dashboard**

Now that Kubernetes is fully up and running unfortunately it doesnt automatically enables any console or dashboard for you. Sometime its easier to check the web console, especially for demos or presentations, here is how we can enable web console / dashboard for Kubernetes.
