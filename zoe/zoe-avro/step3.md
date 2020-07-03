We can now start using zoe to interact with our local Kafka cluster.

## Create the `input-events-topic` topic

The first step is to create the topic that will host our sample data. To do that execute the following command: `zoe topics create input --partitions 5`{{execute}}.

Ensure the topic is created by listing all the topics: `zoe -o table topics list`{{execute}}.

Notice that when creating the topic, we used the topic alias `input` and zoe replaced it with the real name of the topic as described in the configuration.

## Register the avro schema for the cat facts sample dataset

In this guide, we are going to use a sample dataset downloaded from the Cat Facts API. We have also created for the purpose of this guide an avro schema that describes this data. You can take a look at this schema using: `cat schema.avdl`{{execute}}.

Register this schema using the following command:

```
# deploy the cat facts schema from the 
zoe schemas deploy \
  --avdl \
  --from-file schema.avdl \
  --name CatFact \
  --strategy topic \
  --topic input \
  --suffix value
```{{execute}}

Ensure our schema is successfully registered by listing the schemas from the schema registry: `zoe --silent -o table schemas list`{{execute}}

You can also describe the registered schema using: Describe the schema using: `zoe --silent -o table schemas describe input-events-topic-value`{{execute}}.

If the output doesn't fit the screen, you can pipe the previous command into `| less -S`.

## Next step

In the next step, we will produce some avro data into the topic.
