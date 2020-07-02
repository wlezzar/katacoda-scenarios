We can now start using zoe to interact with our local Kafka cluster.

## Create the cat-facts topic

Execute the following command to create a topic named `cat-facts`: `zoe topics create cat-facts --partitions 5`{{execute}}.

Ensure the topic is created: `zoe topics list`{{execute}}.

To print the previous command as a table: `zoe -o table topics list`{{execute}}.

Zoe can use the table output in all the commands.

## Produce some cat facts data

This environment provides a json file containing a sample dataset coming from the Cat Facts API.

You can inspect this file using: `head -n 20 data.json`{{execute}}.

To insert this data into kafka execute the following command: `zoe -o table topics produce --topic cat-facts --from-file data.json`{{execute}}.

## Next step

In the next step, we will see how to read data with Zoe.
