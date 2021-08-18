## Overview

Use the Exchange Maven Facade API to interact with Exchange by using the Maven client to publish and consume Exchange assets as Maven dependencies. Use the Exchange Maven Facade API v3 to publish any type that can be published using [Mule Maven Plugin ](https://docs.mulesoft.com/mule-runtime/4.3/mmp-concept), including Mule 4 applications, templates, examples, and policies. Additionally, you can publish custom assets.

Using the Exchange Maven Facade API version 3 to publish assets to Exchange requires the Mule Maven plugin version 3.5.0 or later.

## Differences between versions 1, 2, and 3

Maven Facade version 1 supports publishing and consuming Exchange assets as Maven dependencies, including apps, templates, examples, connectors, and policies. Maven Facade version 2 supports consuming RAML API specifications.

Maven Facade API version 3 is powered by our new publication engine and supports all current features, including custom assets and publication feedback.

To integrate a Maven client with Maven Facade API version 3, configure a Maven plugin to execute the necessary publication tasks. During the publication process, the API displays its status. If a publication fails, the API displays a list of user friendly errors explaining the problem. After a publication completes successfully, the API provides a link to the published asset.

Maven Facade API must be used through Maven plugins, and not as a REST API.

## Supported types

### Use mule-maven-plugin to publish Mule 4 assets, including:

- Mule applications
- Templates
- Examples
- Policies

### Use exchange-mule-maven-plugin to publish:

- Custom assets

## API Prerequisites and Dependencies

- This API requires an Anypoint Platform account.
- To configure a Maven client, set your Anypoint Platform username and password in this file: `~/.m2/settings.xml`
- To publish an asset with this API, your Anypoint Platform account must have the role Exchange Contributor or the role Exchange Administrator.
- This API works with Mavenized projects, including Mule 4 applications, templates, examples, connectors, and policies.
