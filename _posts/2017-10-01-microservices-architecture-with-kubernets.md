---
layout: post
title: Microservices architecture with Kubernets
subtitle: 3 min read
category: technology
tags: [Kubernetes, Docker, Microservice, Discovery]

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

```java
$ minikube start
$ minikube status

minikube: Running
cluster: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100
```

Run this command to open the Kubernetes dashboard:

```
minikube dashboard
```

Check Kubernetes nodes -

```java
$ kubectl get nodes
NAME       STATUS    AGE       VERSION
minikube   Ready     6d        v1.7.5
```

**Deploying a Containerized App**

There are two ways one can do this, by using Minikube/Kubernetes dashboard or using Kubectl CLI interface.

Create a deployment by clicking the + symbol from right top;

![Create Deployment](https://3.bp.blogspot.com/-Dv5NdI0ZfG8/WdEvOQNr8aI/AAAAAAAACe0/vgfrfE7YCvMi2F7xxN6b1jJD6wrtd8hBgCLcBGAs/s1600/Overview%2B%2B%2BKubernetes%2BDashboard.png)

Provide details and location of your image from Docker Hub;
![Provide details](https://2.bp.blogspot.com/-XGi4BX3przQ/WdEvmHXLIJI/AAAAAAAACe4/TIyLLwVUBe48pJkkyD4fPdra-rhsbPZEACLcBGAs/s1600/Create%2Ban%2Bapp%2B%2B%2BKubernetes%2BDashboard.png)

If all goes well, you should then see Deployment, Pods, Service created properly. Note, I'm using it as a External Service, in a production setup you may have to expose service in a more controlled and secure manner, more on this in separate post later...hopefully soon.

![Dashboard](https://2.bp.blogspot.com/-HvZxb21Gau8/WdEwVUzQGvI/AAAAAAAACfE/w1EGBRlRmGIib7dXcVGXx0OVAzDGiKqsgCLcBGAs/s1600/Workloads%2B%2B%2BKubernetes%2BDashboard.png)

![Dashboard](https://2.bp.blogspot.com/-P9UDBkQJV7M/WdEwR8yZVII/AAAAAAAACfA/wEAoIw-q7301DbmkiU0vD45rh5qUAJOigCLcBGAs/s1600/service%2B%2B%2BKubernetes%2BDashboard.png)

Here I've deployed a SpringBoot microservice "internalapis" which is consumed by a web app "frontend".

You can get external ports for your local services using-

```java
$ kubectl get service
NAME              CLUSTER-IP   EXTERNAL-IP   PORT(S)          AGE
hello-minikube    10.0.0.221   <nodes>       8080:30598/TCP   6d
internalapis      10.0.0.191   <pending>     9000:32342/TCP   4d
kubernetes        10.0.0.1     <none>        443/TCP          6d
newway-frontend   10.0.0.33    <pending>     3000:31247/TCP   2d
```

And to test services - 

http://192.168.99.100:32342/internalapis/users

![API Output](https://4.bp.blogspot.com/-_fTuKjt0h9I/WdEx3wSKjwI/AAAAAAAACfQ/AJfevqqxSfUb2wogrA2iLKSuDChqhvQvQCLcBGAs/s1600/internalapis%2Busers.png)

Test web app -
http://192.168.99.100:31247/frontend

![App Output](https://1.bp.blogspot.com/-slD36eAGnYY/WdEyOXDFKsI/AAAAAAAACfU/pO29IcDrkjUJE5v6GQRfG3_oxJNw1lnLwCLcBGAs/s1600/MP%2BFrontend.png)

Hope this helps to get started.

This can also be achieved using Kubectl commands - [https://kubernetes.io/docs/tutorials/kubernetes-basics/](https://kubernetes.io/docs/tutorials/kubernetes-basics/)
