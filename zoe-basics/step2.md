Zoe relies on central configuration files to know about the different clusters it can interact with. These files are by default stored in: `$HOME/.zoe/config`.

Zoe's repository contains a good starter config file that we can use in this tutorial. To initialize zoe's configuration with this directory, execute:

```
zoe config init \
    --from git \
    --url https://github.com/adevinta/zoe \
    --dir docs/guides/simple/config
```{{execute}}

You can inspect this file with: `cat $HOME/.zoe/config/default.yml`{{execute}}.

You can also check that zoe is now aware of this configuration file by executing: `zoe -o table config clusters list`{{execute}}.

This initial configuration file is good enough to start basic interaction with a local Kafka cluster, let's start having fun! Go to the next step to create our first topic and put some data in it!
