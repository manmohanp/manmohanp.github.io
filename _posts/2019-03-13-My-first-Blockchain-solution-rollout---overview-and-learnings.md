---
layout: post
title: My first Blockchain solution rollout - overview and learnings
subtitle: 5 minute read
category: technology

---

![Blockchain Rollout](https://manmohanp.github.io/assets/img/blockchain-hitesh-choudhary-JNxTZzpHmsI-unsplash.jpg)
First of all, it was great to see one of my initial concept and solution going live on blockchain. It was quite a journey to see from building the concept with initial PoC to finally seeing it through to production. Great teamwork to implement something new and challenging.

The business scenario was to build a service assurance system for telco with the ability to extend it for much wider scenarios like revenue assurance, fraud, and so on. And we took the initial phase of the platform to live that provides the base and an MVP for revenue assurance & operations optimisation for certain service asset.

**Solution Brief:**

At the core, the solution is based on Hyperledger Fabric (1.2) deployed on a Kubernetes cluster on a public cloud infrastructure platform. We had to set up pretty much everything due to choice/availability or rather limitation of the cloud platform (not ideal but what's available).

A high-level view of the solution as below;

![Solution Overview](https://manmohanp.github.io/assets/img/first-blc-solution-overview.jpeg)

Kubernetes version 1.12.4 was used with Docker version 18.6.1 for various containerised components of the solution. For monitoring resource usage KPIs, Prometheus node exporter and kube-state metrics daemon sets were configured. We used Hyperledger Composer framework to manage the blockchain business network.

Tiller + Helm was used to managing the deployment of applications in Kubernetes.

For business reports own framework was built using ReactJS that is pulling data from MongoDB (updated based on event triggers from blockchain) via set of reporting microservices. Peer network used a set of microservices to interface with blockchain.

**Learnings/challenges**

- Getting the data structure, chain code right is key for the future extension also could lead to major re-work and almost dumping everything and starting again with Genesis block!
- Hyperledger documentation could be very confusing, easy to get lost at times
-  If you are planning to roll out or augment this sort of system with an existing platform or business then the key is to make sure you are considering how the initial data blocks and in-flight blocks setup work
- Due to an open bug in Hyperledger fabric, Kafka can't be purged, retention is set as -1 which is forever and needs lots of disk space
- Faced performance issue using CouchDB for the chain, especially using within Docker container, slowness while doing block validation and commit. Ended up using LevelDB which is way faster but with the limitation that queries can only be based on predefined keys rather than any field.
- While setup, if you make mistakes there is a high chance that you cant recover or re-install and resume. Due to how Hperledger is using CouchDB (or LevelDB) and Kafka message persistence, we faced various issues around this area.

We learnt a lot part of this, sometimes it was hard to get to a solution to numerous problems we faced but this learning will help to do things better the next time. I'm sure there are other better ways things could have been done, in the ever-changing world. I myself have seen how versions of some of these core tools and frameworks undergoing massive changes release-on-release.

Looking forward to the next big thing & challenge!! Thanks.

*Note: logos and images used belongs to said organisation, this is used purely for knowledge sharing purpose.*

My other articles on Blockchain -

[Blockchain and Analytics: Unlocking New Billing Opportunities for CSPs](https://www.theblockchaindomain.info/topics/apps-and-use-cases/articles/438937-blockcha-and-analytics-unlocking-new-billing-opportunities-csps.htm)

[Blockchain, Sidechain, Pegged Sidechain, Two-way peg](https://manmohanp.github.io/technology/2018/09/28/Blockchain-Sidechain-Pegged-Sidechain-Two-way-peg.html)

