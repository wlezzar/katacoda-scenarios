We can now start using zoe to interact with our local Kafka cluster.

## Create the cat-facts topic

The first step is to create our input topic that will host our data. To do that execute the following command: `zoe topics create input --partitions 5`{{execute}}.

To print the previous command as a table: `zoe -o table topics list`{{execute}}.

Notice that we have used the topic alias `input` and zoe replaced it with the real name of the topic as described in the configuration.

## Create the avro schema for the cat facts

In this guide, we are gonna a sample data set downloaded from the Cat Facts API. We have also create for the purpose of this guide an avro schema that describes this data. You can take a look at it using: `cat schema.avdl`{{execute}}.

Register this schema using the following command:

```bash
# deploy the cat facts schema from the 
zoe schemas deploy \
  --avdl \
  --from-file schema.avdl \
  --name CatFact \
  --strategy topic \
  --topic input \
  --suffix value
```
{{execute}}.


This environment provides a json file containing a sample dataset coming from the Cat Facts API.

You can inspect this file using: `head -n 20 data.json`{{execute}}.

To insert this data into kafka execute the following command: `zoe -o table topics produce --topic cat-facts --from-file data.json`{{execute}}.

## Next step

In the next step, we will see how to read data with Zoe.
