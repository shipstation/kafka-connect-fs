This is a Shipstation fork of https://github.com/mmolimar/kafka-connect-fs

It patches up a couple things for use in our environment. See commits on master of this fork to see what. At the time of this writing, it was to fix up a few dependency versions and prevent OOMs in the connector when using it against large numbers of files in S3.

Packing it up for use in Kafka Connect (assuming you have the `infrastructure` repo checked out at `~/Projects/`):

```
<change things>
mvn clean package
cp target/kafka-connect-fs-0.3-SNAPSHOT-package/share/java/kafka-connect-fs/* ~/Projects/infrastructure/kubernetes/servicedefs/confluent-platform/kafka-connect/jars/kafka-connect-fs/
```

...then go over to `~/Projects/infrastructure/kubernetes/servicedefs/confluent-platform/kafka-connect` and run `./build-and-push.sh` to get it into our Kafka Connect docker image.
