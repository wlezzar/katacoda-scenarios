The first step of this scenario is to prepare the environment by:

- Spinning up a single node Kafka cluster
- Installing zoe

## Spin up Kafka

To spin up a single node kafka cluster, execute: `docker-compose -f assets/docker-compose.yml up -d`{{execute}}

Wait until the cluster is up and ready: `docker-compose -f assets/docker-compose.yml ps`{{execute}}

## Install Zoe

1. Choose a version for zoe (pick the most recent from the [releases](https://github.com/adevinta/zoe/releases)): `ZOE_VERSION=0.24.0`{{execute}}.
2. Download the zoe debian package: `curl -L "https://github.com/adevinta/zoe/releases/download/v${ZOE_VERSION}/zoe_${ZOE_VERSION}-1_amd64.deb" -o /tmp/zoe.deb`{{execute}}.
3. Install it on the host: `sudo dpkg -i /tmp/zoe.deb`{{execute}}
4. Include Zoe into the path: `export PATH="$PATH:/opt/zoe/bin"`{{execute}}

Check that zoe is installed correctly by printing the help message: `zoe --help`{{execute}}

You are now ready to use Zoe! Go to the next step to start!
