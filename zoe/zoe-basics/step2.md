Zoe relies on central configuration files to know about the different clusters it can interact with. These files are by default stored in: `$HOME/.zoe/config`.

First step is to provide zoe with a configuration file it can use to interact with our local kafka cluster. Zoe's repository contains a good starter config file that we can use here. To initialize zoe's configuration with this configuration, execute the following command:

```
zoe config init \
    --from git \
    --url https://github.com/adevinta/zoe \
    --dir examples/config/basic
```{{execute}}

You can inspect this file with: `cat $HOME/.zoe/config/default.yml`{{execute}}.

If you want some explanations about this configuration, you can take a look at [the longer version of this guide here](https://github.com/adevinta/zoe/blob/master/docs/guides/simple/guide.md#configure-zoe).

You can also check that zoe is now aware of this configuration file by executing: `zoe config clusters list`{{execute}}.

You can print the previous command result as a table by adding `-o table`: `zoe -o table config clusters list`{{execute}}.

This initial configuration file is good enough to start basic interaction with a local Kafka cluster, let's start having fun! Go to the next step to create our first topic and put some data in it!
