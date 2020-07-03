Let's configure zoe to use against our kubernetes hosted Kafka cluster.

Zoe's repository contains a good starter config file that we can use in this tutorial. To initialize zoe with this configuration, execute the following command:

```
zoe config init \
    --from git \
    --url https://github.com/adevinta/zoe \
    --dir examples/config/kubernetes
```{{execute}}

You can inspect this file with: `cat $HOME/.zoe/config/default.yml`{{execute}}.

Notice the `bootstrap.servers` property above pointing to `broker:9092`. We are using the actual broker [Service](https://github.com/adevinta/zoe/blob/master/docs/guides/kubernetes/resources/broker-service.yaml) name defined in kubernetes. This DNS name is only visible inside the kubernetes cluster. Zoe will be able to reach it because we will be using the kubernetes runner that spins up the consumers, producers and all the kafka clients as pods inside the cluster. So the internal kubernetes DNS names are visible and usable.

You can also check that zoe is now aware of this configuration file by executing: `zoe -o table config clusters list`{{execute}}.

Everything looks good! You can continue to the next step!
