We can now start using zoe to interact with our local Kafka cluster.

## Create the cat-facts topic

The first step is to create our input topic that will host our data. To do that execute the following command: `zoe topics create input --partitions 5`{{execute}}.

To print the previous command as a table: `zoe -o table topics list`{{execute}}.

Notice that we have used the topic alias `input` and zoe replaced it with the real name of the topic as described in the configuration.

## Create the avro schema for the cat facts

In this guide, we are going to use a sample data set downloaded from the Cat Facts API. We have also create for the purpose of this guide an avro schema that describes this data. You can take a look at this schema using: `cat schema.avdl`{{execute}}.

Register the schema using the following command:

```
# deploy the cat facts schema from the 
zoe schemas deploy \
  --avdl \
  --from-file schema.avdl \
  --name CatFact \
  --strategy topic \
  --topic input \
  --suffix value
```{{execute}}.

Ensure our schema is successfully registered by listing the topics from the schema registry: `zoe --silent -o table schemas list`{{execute}}.

You can also describe the registered schema using: Describe the schema using: `zoe --silent -o table schemas describe input-events-topic-value`{{execute}}.

## Next step

In the next step, we will produce some avro data into the topic.
