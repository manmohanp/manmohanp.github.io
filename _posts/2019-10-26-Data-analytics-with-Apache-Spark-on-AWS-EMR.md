```
---

layout: post
title: Data analytics with Apache Spark on AWS EMR
subtitle: 8 min read
category: technology
hide: true
tags: [Data Analytics, Apache Spark, Spark, AWS, EMR, Big Data]

---
```

A simple demonstration of **Apach Spark** for data analysis running on **AWS EMR (Elastic Map Reduce)** cluster setup. I'm using pyspark but its very similar to Spark scala or Java (I did it on both Python and Java but for this writeup I am using Python)

**AWS EMR** is a managed big data platform that provides a cluster to run jobs across cluster without having to worry about setting up the cluster, etc. We can use Spark & other frameworks on EMR. Not dwelling too much in to details of EMR or Spark jobs in this writeup, there are enough materials on official sites or other blogs. This is mostly a log of things that I did and managed to run the setup/jobs for my need for demo purpose.

Not going in to details of basic AWS account, billing, etc setup that you will need, before getting started you will need;

* An AWS account with billing setup - some of the services that I've used are chargable by AWS, so should delete when done
* Have your spark job ready and tested locally (on your laptop or some single node machine)



**Setup a AWS S3 bucket**

Create a S3 bucket to store your input data files, outputs, logs, configs, etc.

![s3-bucket](https://manmohanp.github.io/assets/img/s3-bucket.png)

**Setup a AWS key pair**

Under EC2 > Key Pairs create a key pair with some name like emr-key. This should generate a key (emr-key.pem) file and gets downloaded. Save it somewhere safe on your local machine.

**Setup AWS EMR Cluster**

Search for EMR on AWS console, then create cluster. Select/configure hardware, software and security required for the cluster.

On the next screen, Go to quick options.

![emr-cluster-software](https://manmohanp.github.io/assets/img/emr-cluster-software.png)



Then select required hardware.

![emr-cluster-hardware](https://manmohanp.github.io/assets/img/emr-cluster-hardware.png)



Provide name of the cluster and in my case added a custom config to initialise optional software needed for future.

![emr-cluster-nameconfig](https://manmohanp.github.io/assets/img/emr-cluster-nameconfig.png)

Add security key pair;

![emr-cluster-security](https://manmohanp.github.io/assets/img/emr-cluster-security.png)

Then once you hit Create cluster it should then start, bootstrap any custom actions and start your cluster i.e. in our case 1 master and 2 worker/core nodes.

![emr-cluster-ready](https://manmohanp.github.io/assets/img/emr-cluster-ready.png)

