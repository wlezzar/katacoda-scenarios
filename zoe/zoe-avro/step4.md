Let's produce some Avro data into the topic.

## Producing data

Now that we have the Cat Facts Avro schema registered, let's produce some cat facts from the `data.json` file in avro:

```
zoe --silent -o table topics produce \
    --topic input \
    --from-file data.json \
    --subject input-events-topic-value
```{{execute}}

We could have omitted the `--subject` option as we have already told zoe about that topic's subject name in the configuration (see above).

When zoe sees that we are using the `KafkaAvroDeserializer`, it automatically tries to convert data from json into Avro [Generic Records](https://avro.apache.org/docs/1.7.6/api/java/org/apache/avro/generic/GenericRecord.html) before supplying them to the producer.

## Next step

In the next step, we will see how to read data with Zoe.
