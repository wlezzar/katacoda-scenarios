We can now start using zoe to interact with our Kubernetes hosted Kafka cluster.

## Create the cat-facts topic

Create a topic called `cat-facts` (As we are using the kubernetes runner, this first run will download the `zoe` docker image so expect it to be slower than the subsequent calls): `zoe topics create cat-facts --partitions 5`{{execute}}

Ensure the topic is created: `zoe -o table topics list`{{execute}}.

If you want to see what's happening behind the scenes and how zoe spins up the pods, increase the verbosity level: `zoe -vv -o table topics list`{{execute}}

## Produce some cat facts data

This environment provides a json file containing a sample dataset coming from the Cat Facts API.

You can inspect this file using: `head -n 20 data.json`{{execute}}.

To insert this data into kafka execute the following command: `zoe -o table topics produce --topic cat-facts --from-file data.json`{{execute}}.

## Consuming data

You can read data using the following command: `zoe -o table topics consume cat-facts --from 'PT1h' -n 5`{{execute}}

## Parallelizing the consumption across multiple pods

Now imagine we want to find cat facts we received in the previous six hour, written by the user whose first name is `Kasimir`. Also, imagine we are dealing with a large topic and we want to parallelize our search across multiple pods. With zoe, you can achieve that using:

```
zoe -o table topics consume cat-facts \
       --from 'PT6h' \
       --filter "user.name.first == 'Kasimir'" \
       --jobs 3 \
       -n 5
```{{execute}}

The above command spins 3 pods consuming the topic in parallel to increase the speed of the search. This is obviously overkill in this case as we have a small dataset but this is extremely useful when dealing with large topics.
