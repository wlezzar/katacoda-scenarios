In this step, we will cover how to read Avro data from kafka using zoe.

## Read data from an Avro Topic

Reading data from an Avro topic with zoe is really no different from reading a Json topic. Zoe seemlessly transforms avro data into json and can apply the jmespath filters with `--filter` as with json data. In fact the following command works exactly the same in both this guide and the [Basic scenario](../simple/guide.md):

```
zoe --silent -o table topics consume input \
       -n 10 \
       --from 'PT1h' \
       --query '{id: _id, type: type, user: user, upvotes: upvotes}' \
       --filter "user.name.first == 'Kasimir'"
```{{execute}}

Or using `jq`:

```
zoe --silent -o table topics consume input \
       -n 10 \
       --from 'PT1h' \
       --dialect jq \
       --query '{_id, type, user, upvotes}' \
       --filter '.user.name.first == "Kasimir"'
```{{execute}}