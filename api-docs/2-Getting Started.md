## Configure Maven

Create a maven client settings file: `~/.m2/settings.xml`

### Use Anypoint Platform credentials

Configure your credentials for the Exchange Maven Facade API:

```
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 
http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <servers>
    <server>
      <id>Repository</id>
      <username>USERNAME</username>
      <password>PASSWORD</password>
    </server>
  </servers>
</settings>
```

The `<id>` value is arbitrary, but must have the same value in your pom.xml and settings.xml files. The `<server> ... <id>` value in the settings.xml file is the same value as the `<repository> ... <id>` value in the pom.xml file.

### Use an Access Token

Exchange Maven Facade supports using a Core Services access token instead of a username and password.

Obtain a token with this [request](https://anypoint.mulesoft.com/exchange/portals/anypoint-platform/f1e97bc6-315a-4490-82a7-23abe036327a.anypoint-platform/access-management-api/minor/1.0/console/method/#7573/)

Alternatively, if you sign in with an identity provider (IdP), you can use your IdP token.

In the file `settings.xml` , specify the special user `~~~Token~~~`.

Replace `ACCESS_TOKEN` with the Core Services access token.

```
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
 http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <servers>
    <server>
      <id>Repository</id>
      <username>~~~Token~~~</username>
      <password>ACCESS_TOKEN</password>
    </server>
  </servers>
</settings>
```

## Publish with Maven

Successful publication using the Maven Facade API version 3 requires configuring the Maven plugin correctly.

The plugin performs these actions:

- Before uploading the asset's files, validate that the asset can be created, including checking asset ID availability.
- Give the publication status.
- When all files have finished uploading, mark the asset publication complete.

These examples show how to configure your POM file.

For complete examples, see the section [Examples](../Examples)).

### Use mule-maven-plugin to publish Mule 4 assets

The latest version of this plugin is `3.5.0`.

This example shows the `build` section of `pom.xml`.

This example packages a `mule-application` asset.

```
    <build>
        <plugins>
            <plugin>
                <groupId>org.mule.tools.maven</groupId>
                <artifactId>mule-maven-plugin</artifactId>
                <version>3.5.0-SNAPSHOT</version>
                <extensions>true</extensions>
                <configuration>
                    <classifier>mule-application</classifier>
                </configuration>
            </plugin>
        </plugins>
    </build>
```

_ Note: _`mule-maven-plugin`_ is integrated with _`exchange-mule-maven-plugin`_._

### Use exchange-mule-maven-plugin to publish Custom assets

The latest version of this plugin is `0.0.13`.

This example shows the `build` section of `pom.xml`.

This example publishes a `custom` asset.

```
     <build>
        <plugins>
            <plugin>
                <groupId>org.mule.tools.maven</groupId>
                <artifactId>exchange-mule-maven-plugin</artifactId>
                <version>0.0.9</version>
                <executions>
                    <execution>
                        <id>validate</id>
                        <phase>validate</phase>
                        <goals>
                            <goal>exchange-pre-deploy</goal>
                        </goals>
                    </execution>
                    <execution>
                        <id>deploy</id>
                        <phase>deploy</phase>
                        <goals>
                            <goal>exchange-deploy</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
```

If the build fails during the deploy stage with a status code of 412 (Precondition Failed), then the `<goal>exchange-pre-deploy</goal>` has not been executed. To fix this error, ensure that goal is set inside the executions section of the plugin.

The error looks similar to this:

```
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.871 s
[INFO] Finished at: 2020-11-09T12:11:54-03:00
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-deploy-plugin:2.7:deploy (default-deploy) on project hello-world-pom: Failed to deploy artifacts: Could not transfer artifact 1da12ec1-7614-43a3-bf24-ff754cab8ddf:hello-world-pom:pom:1.0.3 from/to repository-id ([https://maven.anypoint.mulesoft.com/api/v3/organizations/orgId/maven/](http://localhost:8088/api/v3/organizations/1da12ec1-7614-43a3-bf24-ff754cab8ddf/maven/)): Transfer failed for [https://maven.anypoint.mulesoft.com](http://localhost:8088/api/v3/organizations/1da12ec1-7614-43a3-bf24-ff754cab8ddf/maven/)[/api/v3/organizations/](http://localhost:8088/api/v3/organizations/1da12ec1-7614-43a3-bf24-ff754cab8ddf/maven/1da12ec1-7614-43a3-bf24-ff754cab8ddf/hello-world-pom/1.0.3/hello-world-pom-1.0.3.pom)[orgId](http://localhost:8088/api/v3/organizations/1da12ec1-7614-43a3-bf24-ff754cab8ddf/maven/)[/maven/groupId/assetId/version/filename](http://localhost:8088/api/v3/organizations/1da12ec1-7614-43a3-bf24-ff754cab8ddf/maven/1da12ec1-7614-43a3-bf24-ff754cab8ddf/hello-world-pom/1.0.3/hello-world-pom-1.0.3.pom) 412 -> [Help 1]
```

## Consume with Maven

To consume an asset published in Exchange using Maven, edit your POM file. In the repositories section, add the Exchange Maven Facade as a repository. In the dependencies section, add the groupId, artifactId (assetId), and version of the asset to use as a dependency.

For example:

```
<project xmlns="http://maven.apache.org/POM/4.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
[...]

  <dependencies>
    <dependency>
      <groupId>org.mule.modules</groupId>
      <artifactId>mule-module-sfdc</artifactId>
      <version>8.0.0-SNAPSHOT</version>
    </dependency>
  </dependencies>

[...]

  <repositories>
    <repository>
      <id>Repository</id>
      <name>Corporate Repository</name>
    <url>https://maven.anypoint.mulesoft.com/api/v3/maven</url>
      <layout>default</layout>
    </repository>
  </repositories>
[...]
</project>
```
