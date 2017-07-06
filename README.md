# Fuse Integration Services (FIS) Trace Transformer Endpoint

This example demonstrates how you can use a Trace Transformer endpoint in Apache Camel with Spring Boot.

The quickstart uses Spring Boot to configure a little application that includes a Camel route that sets a static body, transforms it using a sample map in Trace Transformer, and logs the resulting Camel body.

### Running the example standalone with SpringBoot

#### Prerequisite installation steps

In order to run this example, a evaluation license must be obtained from [Trace Financial](https://www.tracefinancial.com/contact-us).  For the purpose of this example, Transformer version 3.6.3 is assumed.  Once the Transformer tooling has been downloaded, please execute the following steps to copy the required files to your local Maven repository:

1. Copy <transformer-install-dir>\runtime\3.6.3\single\transformer-runtime-with-log4j-3.6.3-complete.jar to a temp directory

2. Copy <transformer-install-dir>\runtime\3.6.3\camel-osgi\transformer-camel-3.6.3-osgi-bundle.jar to a temp directory

3. Copy <transformer-install-dir>\lib\transformer-designtime-3.6.3.jar and <transformer-install-dir>\lib\currencylib-1.0.5.jar to a temp directory

4. Copy the files located in <transformer-install-dir>\maven to a temp directory

5. Execute the following commands via the CLI to install the prerequisite JAR files in your local Maven repostiory:

	mvn install:install-file -DgroupId=com.tracegroup.transformer -DartifactId=transformer-runtime-complete -Dversion=3.6.3 -Dfile=transformer-runtime-with-log4j-3.6.3-complete.jar -Dpackaging=jar

	mvn install:install-file -DgroupId=com.tracegroup.transformer -DartifactId=transformer-camel-osgi -Dversion=3.6.3 -Dfile=transformer-camel-3.6.3-osgi-bundle.jar -Dpackaging=jar

	mvn install:install-file -DgroupId=com.tracegroup.transformer -DartifactId=transformer-designtime -Dversion=3.6.3 -Dfile=transformer-designtime-3.6.3.jar -Dpackaging=jar

	mvn install:install-file -DgroupId=com.tracegroup.transformer -DartifactId=currencylib -Dversion=1.0.5 -Dfile=currencylib-1.0.5.jar -Dpackaging=jar
	
6.  There should be a file in the temp directory called `CamelIntegrationTestSample.zip`.  Extract the project, then copy CamelIntegrationTestSample/SampleTransformerProject/build/SampleTransformerProject-1.0-SNAPSHOT.jar to the temp directory

7. Install the Trace Transformer sample project to your local Maven repository by executing the following command:

	mvn install:install-file -DgroupId=com.acme.messaging -DartifactId=SampleTransformerProject -Dversion=1.0.0 -Dfile=SampleTransformerProject-1.0-SNAPSHOT.jar -Dpackaging=jar

#### Test the example

The example can be demonstrated by running the following command:

    mvn spring-boot:run

### Running the example in OpenShift

It is assumed that:
- OpenShift platform is already running, if not you can find details how to [Install OpenShift at your site](https://docs.openshift.com/container-platform/3.3/install_config/index.html).
- Your system is configured for Fabric8 Maven Workflow, if not you can find a [Get Started Guide](https://access.redhat.com/documentation/en/red-hat-jboss-middleware-for-openshift/3/single/red-hat-jboss-fuse-integration-services-20-for-openshift/)

The example can be built and run on OpenShift using a single goal:

    mvn -P ocp

When the example runs in OpenShift, you can use the OpenShift client tool to inspect the status

To list all the running pods:

    oc get pods

Then find the name of the pod that runs this quickstart, and output the logs from the running pods with:

    oc logs <name of pod>

You can also use the openshift [web console](https://docs.openshift.com/container-platform/3.3/getting_started/developers_console.html#developers-console-video) to manage the
running pods, and view logs and much more.
