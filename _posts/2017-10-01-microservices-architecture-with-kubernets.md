---
layout: post
title: Microservices architecture with Kubernets
category: technology
---

Kubernetes is an open-source platform for [automating deployment, scaling, and operations of application containers](http://www.slideshare.net/BrianGrant11/wso2con-us-2015-kubernetes-a-platform-for-automating-deployment-scaling-and-operations) across clusters of hosts, providing container-centric infrastructure.

Kubernetes enables speed and efficiency to respond to customer demand. Deploy application quickly that is predictable. Scale on the fly, deploy on the fly, zero/near-zero downtime. Optimal server resource utilisation.

More on why Kubernetes - [https://kubernetes-v1-4.github.io/docs/whatisk8s/](https://kubernetes-v1-4.github.io/docs/whatisk8s/)

Kubernetes provides multiple solutions to build, test & deployment locally and on production infrastructure, [more](https://kubernetes-v1-4.github.io/docs/getting-started-guides/).

For the purpose of this post, I'm using a local build & test deployment using Minikube. This is available for OSX & Linux OS. I'm using OSX.

I found Kubernetes interactive documentation is a great way to practice commands side by side while trying to understand & setup Kubernetes cluster & deploying apps - https://kubernetes.io/docs/tutorials/kubernetes-basics/

**Install Minikube**

Latest release [https://github.com/kubernetes/minikube/releases](https://github.com/kubernetes/minikube/releases)

**Install Kubectl**

It is a command line interface for running commands against Kubernetes clusters.

Installation steps - [https://kubernetes.io/docs/tasks/tools/install-kubectl/](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

**Start & Check status of Minikube**

{% highlight java %}
$ minikube start
$ minikube status

minikube: Running
cluster: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100
{% endhighlight %}