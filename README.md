# ariba-p2p-requisition-client

## Overview

The project represents a procure to pay requisition client for SAP Ariba.

You can use the `ariba-p2p-requisition-client` to:

  * submit requisitions to your SAP Ariba instance

## Import the `ariba-p2p-requisition-client` in your project

1. Create a module in your project to place the source code in. (the module contains only pom.xml with the configuration described below)

2. Configure the 'maven-scm-plugin` plugin to pull the source code from the GitHub repo.

  ```
  <scm>
    <connection>scm:git:git://github.com/svilenkomitov/ariba-p2p-requisition-client.git</connection>
    <developerConnection>scm:git:https://github.com/svilenkomitov/ariba-p2p-requisition-client.git</developerConnection>
    <url>https://github.com/svilenkomitov/ariba-p2p-requisition-client</url>
  </scm>
  ```

2. Add the property specifying the `maven-scm-plugin` version to be used.

  ```
  <properties>
  ...
  	<maven.scm.plugin.version>1.9</maven.scm.plugin.version>
  ...
  </properties>
  ```

3. Add the `maven-scm-plugin` and its configuration.

	```
	<build>
		<plugins>
	  ...
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-scm-plugin</artifactId>
				<version>${maven.scm.plugin.version}</version>
				
				<configuration>
					<goals>checkout</goals>
					<!-- the dir path to pull the changes in -->
					<checkoutDirectory>${project.basedir}/src/main/java</checkoutDirectory> 
					<workingDirectory>${project.basedir}/src/main/java</workingDirectory>
					<!-- include only the source code -->
					<includes>ariba/**</includes> 
				</configuration>
				
				<executions>
					<execution>
						<id>generated-sources</id>
						<phase>generate-sources</phase>
						<goals>
							<goal>checkout</goal>
						</goals>
					</execution>
				</executions>
				
			</plugin>
		...
		</plugins>
	</build>
	```
