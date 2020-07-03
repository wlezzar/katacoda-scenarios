Let's configure zoe to use against our local Schema Registry enabled Kafka cluster.

Zoe's repository contains a good starter config file that we can use in this tutorial. To initialize zoe with this configuration, execute the following command:

```
zoe config init \
    --from git \
    --url https://github.com/adevinta/zoe \
    --dir examples/config/avro
```{{execute}}

You can inspect this file with: `cat $HOME/.zoe/config/default.yml`{{execute}}.

If you want some explanations about this configuration, you can take a look at [the longer version of this guide here](https://github.com/adevinta/zoe/blob/master/docs/guides/avro/guide.md#configure-zoe).

You can also check that zoe is now aware of this configuration file by executing: `zoe -o table config clusters list`{{execute}}.

Notice that we have defined a topic alias `input` that points to the real topic name `input-events-topic`. We can use topic aliases and real topic names interchangeably in most of the commands involving topics.

Everything looks good! You can continue to the next step!
