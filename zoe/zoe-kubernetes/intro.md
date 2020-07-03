This tutorial shows how you can use zoe to interact with Kafka using the Kubernetes remote runner. With this runner, instead of spinning up the consumers / producers in the caller's machine, zoe spins them up as kubernetes pods. This is extremely useful when dealing with a cloud hosted Kafka cluster that is only reachable from that Kubernetes cluster or when you want to be able to parallelize your topic consumption / search across several pods.

If you are new to zoe, we recommend you start with [the basic scenario](https://www.katacoda.com/wlezzar/scenarios/zoe-basics).

## What you will learn

In this guide, you will learn the following aspects of zoe:

- Using the Kubernetes runner to interact with a Kubernetes hosted Kafka cluster.
- Listing and describing topics.
- Reading json data from kafka using multiple consumer pods to scan the topics faster.
