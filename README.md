
# What is this?

This is a fork of original stash-log4j-jsonevent-layout, but I modify it so that it is packaged as a JBoss Fuse fragment bundle and attach to `org.ops4j.pax.logging.pax-logging-service`.

More docummentation around how to configure your log4j so as to output JSON logs, refer to https://github.com/logstash/log4j-jsonevent-layout

# How to build

```bash
$ mvn clean package install
```

Now this bundle will be installed into local Maven repository.

# Install to JBoss Fuse

```bash
JBossFuse:karaf@root> osgi:install mvn:net.logstash.log4j/jsonevent-layout/1.8-SNAPSHOT
undle ID: 1946
JBossFuse:karaf@root> refresh
JBossFuse:karaf@root> osgi:list  | grep 'layout'
[1946] [Resolved   ] [            ] [       ] [   60] jsonevent-layout (1.8.0.SNAPSHOT), Hosts: 3
```

Now this fragment should be loaded into Fuse. The `Resolved` status means it has attached to Host:  `org.ops4j.pax.logging.pax-logging-service`.

Configure <FUSE_HOME>/etc/org.ops4j.pax.logging.cfg, and check data/log/fuse.log and see if output JSON logs.