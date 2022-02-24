# Softalks Maven archetypes
There are four parameters of the [archetype:generate](https://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html) goal that can be preconfigured in the [.mvn/jvm.config](https://maven.apache.org/configure.html#mvn-jvm-config-file) file. All of them are required to create a project based on an archetype provided by this repository. The parameters **archetypeGroupId**, **archetypeArtifactId** and **archetypeVersion** (this one defaulting to **1.0-SNAPSHOT**) define the archetype to be used. The **archetypeCatalog** parameter should have always the value ***local*** to avoid an unnecesary (and slow) query to the Maven Central archetype registry

This is a valid content for that file (or a set of command line arguments) selecting one of this repositories' archetypes:
```
-DarchetypeGroupId=com -DarchetypeArtifactId=softalks.archetypes.void -DarchetypeVersion=1.0 -DarchetypeCatalog=local
```
The rest of mandatory arguments can be predefined using a properties file (let's say is called **args.properties**):
```
archetypeGroupId=com
archetypeArtifactId=softalks.archetypes.void
archetypeVersion=1.0-SNAPSHOT
groupId=com
artifactId=softalks.archetypes.void
version=0.9-SNAPSHOT
package=unnecessary # only used for jar packaging but always required
```
And running:
```
mvn archetype:generate -Darchetype.properties=args.properties
```
Before using any of the archetypes defined in this project you must set up your [settings.xml](https://maven.apache.org/settings.html) file like this:
```
<?xml version="1.0" encoding="UTF-8"?>
<settings 
	xmlns="http://maven.apache.org/SETTINGS/1.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <servers>
    <server>
      <id>archetype</id>
      <username>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</username>
      <password>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</password>
    </server>
  </servers>
  <profiles>
    <profile>
      <id>github</id>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>
      <repositories>
        <repository>
          <id>archetype</id>
          <url>https://maven.pkg.github.com/softalks/archetypes</url>
          <snapshots>
            <enabled>true</enabled>
          </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>
</settings>
```
