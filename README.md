hello-samza-base
===========

Hello Samza Base is based on Samza's [Hello Samza](https://github.com/apache/samza-hello-samza) project (based on [apache/samza-hello-samza@`2214946`](https://github.com/apache/samza-hello-samza/tree/2214946c0b5498f9942e4ecdd4327fea4081b689)).

It removes the bootstrapping and cluster-management tools to serve as a boilerplate from which you can create your own simple Samza tasks.

### Running Hello Samza Base

To run, you must have the existing Hello Samza infrastructure set up. Once that is ready, you can compile the tasks here and run them on the existing cluster.

```sh
mvn clean package
mkdir -p deploy/samza
tar -xvf ./target/hello-samza-0.10.1-dist.tar.gz -C deploy/samza
deploy/samza/bin/run-job.sh --config-factory=org.apache.samza.config.factories.PropertiesConfigFactory --config-path=file://$PWD/deploy/samza/config/wikipedia-feed.properties
deploy/samza/bin/run-job.sh --config-factory=org.apache.samza.config.factories.PropertiesConfigFactory --config-path=file://$PWD/deploy/samza/config/wikipedia-parser.properties
deploy/samza/bin/run-job.sh --config-factory=org.apache.samza.config.factories.PropertiesConfigFactory --config-path=file://$PWD/deploy/samza/config/wikipedia-stats.properties
```

### Make it your own

There are some customizations you should do to make this repository your own.

1. Update pom.xml with your project, version, organization, and developer details.
  * This will change the deploy commands above. E.g. `hello-samza` and `0.10.1` are driven by `artifactId` and `version`.
1. Remove or update LICENSE to match your licensing desires.
1. Remove or update the code under `src/main/java/samza`
1. Remove or update the code under `src/main/config/wikipedia-*.properties`
  * This will change the deploy commands above. E.g. replace `wikipedia-feed.properties` with your new properties file.
1. Update or remove this README.
