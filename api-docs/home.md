## Overview

The Exchange Maven Facade API lets you interact with Exchange using the Maven client to publish and consume Exchange assets as Maven dependencies. You can use the Exchange Maven Facade API v3 to publish any type that can be published using [Mule Maven Plugin ](https://docs.mulesoft.com/mule-runtime/4.3/mmp-concept)for instance Mule 4 applications, templates, examples, and policies. Additionally, you can publish Custom Assets.

### Beta Program

The Exchange Maven Facade API version 3 is in _BETA_. To sign up as a beta tester and test this version before the General Availability (GA) release, sign the Pre-GA License Agreement: [https://www.mulesoft.com/legal/beta-license-sign](https://www.mulesoft.com/legal/beta-license-sign)

After accepting the pre-GA agreement, within 24 hours you will receive an email confirming access to the APIs.

## Differences between versions 1, 2, and 3

Maven Facade version 1 supports publishing and consuming Exchange assets as Maven dependencies, including apps, templates, examples, connectors, and policies. Maven Facade version 2 supports consuming RAML API specifications.

Maven Facade API version 3, currently in BETA, is powered by our new publication engine and supports all current features, including custom assets and publication feedback.

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

_Note: The publication of connectors and extensions will be supported with a similar plugin in an upcoming release._

## API Prerequisites and Dependencies

- This API requires an Anypoint Platform account.
- To configure a Maven client, set your Anypoint Platform username and password in this file: `~/.m2/settings.xml`
- To publish an asset with this API, your Anypoint Platform account must have the role Exchange Contributor or the role Exchange Administrator.
- This API works with Mavenized projects, including Mule 4 applications, templates, examples, connectors, and policies.
