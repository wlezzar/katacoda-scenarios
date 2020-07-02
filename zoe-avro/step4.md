In this step, we will cover how to read data from kafka using zoe.

## Read data from the Cat Facts topic

To read data from the `cat-facts` topic, execute the following command: `zoe --silent topics consume cat-facts -n 10 --from 'PT1h'`{{execute}}.

The command above asks for 10 records (`-n 10`) from data received since one hour ago (`--from 'PT1h'`). We have also deliberately added a `--silent` option to avoid outputting the logs.

We can print the previous data as a table by adding `-o table` (we also pipe data to `less -S` as the table is too big to fit in the screen): `zoe --silent -o table topics consume cat-facts -n 10 --from 'PT1h' | less -S`{{execute}}.

Press the letter `q` to get our from `less -S`.

## Using filters

With Zoe you can filter data using jmespath (by default) or jq expressions. These expressions get executed against each record:

- if the result of the expression is false, the record is discarded.
- otherwise, it's returned back in the results.

As an example: Let's filter out records belonging to the user whose first name is `Kasimir`:

```
zoe  --silent -o table topics consume cat-facts \
       -n 5 \
       --from 'PT1h' \
       --filter "user.name.first == 'Kasimir'"
```{{execute}}

If you want to use jq instead:

```
zoe --silent -o table topics consume cat-facts \
       -n 5 \
       --from 'PT1h' \
       --dialect jq \
       --filter '.user.name.first == "Kasimir"'
```{{execute}}
