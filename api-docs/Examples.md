These examples show how to upload an asset in Exchange using Maven Facade API v3, mule-maven-plugin, and exchange-mule-maven-plugin.

Each example is boilerplate. For successful publication, you must replace the variables that specify the asset, including at least the organizationId (YOUR\_ORG\_ID). The documentation repository includes [a command to replace them automatically](https://github.com/mulesoft-labs/exchange-documentation-samples#configure-the-groupid-of-the-anypoint-organization-where-you-will-be-publishing-assets).

The examples are in this repository: [https://github.com/mulesoft-labs/exchange-documentation-samples](https://github.com/mulesoft-labs/exchange-documentation-samples)

Before running the examples, open a terminal and execute this command to clone the project:

`git clone git@github.com:mulesoft-labs/exchange-documentation-samples.git`

## Upload a mule-app

This project shows how to publish a simple Mule application to Exchange using the Exchange Maven Facade API version 3.

1. Execute this command: `cd exchange-documentation-samples/mule-app`
2. Follow the instructions in this [readme](https://github.com/mulesoft-labs/exchange-documentation-samples/tree/master/mule-app)

## Upload an example

This project shows how to publish a simple Mule application example to Exchange using the Exchange Maven Facade API version 3. It's similar to the Mule application project, but in this example, the asset type is `Example`. Exchange _Examples_ are applications that are ready to run in Anypoint Studio and demonstrate a use case or solution.

1. Execute this command: `cd exchange-documentation-samples/example`
2. Follow the instructions in this [readme](https://github.com/mulesoft-labs/exchange-documentation-samples/tree/master/example)

## Upload a template

This application shows how to publish a simple Mule application template to Exchange using the Exchange Maven Facade API version 3. It's similar to the Mule application project, but in this example, the asset type is `Template`. Exchange _Templates_ are packaged integration patterns built on best practices to address common use cases.

1. Execute this command: `cd exchange-documentation-samples/template`
2. Follow the instructions in this [readme](https://github.com/mulesoft-labs/exchange-documentation-samples/tree/master/template)

## Upload a policy

This project shows how to publish a simple Mule policy to Exchange using the Exchange Maven Facade API version 3.

1. Execute this command: `cd exchange-documentation-samples/policy`
2. Follow the instructions in this [readme](https://github.com/mulesoft-labs/exchange-documentation-samples/tree/master/policy)

## Upload Custom assets

The Exchange Maven Facade API version 3 supports the publication of custom assets.

After you configure the Maven plugin correctly, the plugin will sync with the API to notify it when the publishing process should begin, and will also provide updates on the asset publication’s state until the publication is complete.

### Without files (i.e. parent pom)

This project shows how to publish a simple custom asset that contains only a single POM file. The main use case for this asset type in the Maven experience is uploading a parent POM file to Exchange. Then the file can be used in any type of Maven projects, such as a connector or a Mule application.

1. Execute this command: `cd exchange-documentation-samples/custom-asset`
2. Follow the instructions in this [readme](https://github.com/mulesoft-labs/exchange-documentation-samples/tree/master/custom-asset)

### With files (i.e. Java library)

This project shows how to publish a simple custom asset to Exchange using the Exchange Maven Facade API version 3.

Custom assets can package any Maven reusable component. In this example, the custom asset is a Java library.

1. Execute this command: `cd exchange-documentation-samples/custom-lib`
2. Follow the instructions in this [readme](https://github.com/mulesoft-labs/exchange-documentation-samples/tree/master/custom-asset)
