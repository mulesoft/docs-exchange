## Publish Custom Assets

It is now possible to publish custom assets through the Maven Facade API version 3 by using `exchange-mule-maven-plugin`. Custom assets can package any Maven reusable component, such as a Java library.

You can see examples of use in the Custom asset section [here](../Examples)

## Publication feedback

The Maven Facade API version 3 and the integrated Exchange Maven plugin have improved feedback on publication errors. Maven 3.6 ended support for the field `ReasonPhrase`, so previous versions of the Maven API could only supply an error status code for the request and no description. The new Maven API shows the publication status from start to finish.

### Failure feedback

The plugin prints the step where publication fails and the errors:

```
[INFO]   Publication status: error
[INFO]   ------------------------------------------------------------
[INFO]     Steps:
[INFO]     - Description: Publishing asset
[INFO]     - Status: error
[INFO]     - Errors: [The asset metadata is invalid, Could not find mule-artifact file inside jar file, Could not find classloader-model.json to extract dependencies]
[INFO]     .........................................
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  01:00 min
[INFO] Finished at: 2020-09-22T13:53:23-03:00
[INFO] ------------------------------------------------------------------------
```

### Success feedback

After the publication is finished, the plugin prints the publication status as completed, and provides a link to see the new asset in Exchange:

```
[INFO] Copying file demoplugin-example-1.0.1-status-1600874121893.json to directory /var/folders/jj/bk19q_cn17z29y0mc8c0d4yr65f856/T/1600874121892-0
[INFO]   ------------------------------------------------------------
[INFO]   Publication status: running
[INFO]   ------------------------------------------------------------
[INFO]     Steps:
[INFO]     - Description: Publishing asset
[INFO]     - Status: running
[INFO]     .........................................
[INFO] Getting publication status
Downloading from : https://repository.mulesoft.org/nexus/content/repositories/releases/69dde2e5-61db-41f5-a939-9047995c96ed/demoplugin-example/1.0.1/demoplugin-example-1.0.1-status-1600874127465.json
Downloading from : https://repository.mulesoft.org/nexus/content/repositories/ci-releases/69dde2e5-61db-41f5-a939-9047995c96ed/demoplugin-example/1.0.1/demoplugin-example-1.0.1-status-1600874127465.json
Downloading from : https://maven.anypoint.mulesoft.com/api/v3/organizations/69dde2e5-61db-41f5-a939-9047995c96ed/maven/runId/7506d61d-1707-4b59-b3f1-d79bf8ce9575/69dde2e5-61db-41f5-a939-9047995c96ed/demoplugin-example/1.0.1/demoplugin-example-1.0.1-status-1600874127465.json
Downloaded from : https://maven.anypoint.mulesoft.com/api/v3/organizations/69dde2e5-61db-41f5-a939-9047995c96ed/maven/runId/7506d61d-1707-4b59-b3f1-d79bf8ce9575/69dde2e5-61db-41f5-a939-9047995c96ed/demoplugin-example/1.0.1/demoplugin-example-1.0.1-status-1600874127465.json (122 B at 97 B/s)
[INFO] Copying file demoplugin-example-1.0.1-status-1600874127465.json to directory /var/folders/jj/bk19q_cn17z29y0mc8c0d4yr65f856/T/1600874127465-0
[INFO]   ------------------------------------------------------------
[INFO]   Publication status: completed
[INFO]   ------------------------------------------------------------
[INFO]     Steps:
[INFO]     - Description: Publishing asset
[INFO]     - Status: completed
[INFO]     .........................................
[INFO]
[INFO]   Your asset has been successfully published to Exchange.
[INFO]   You can check it at: https://anypoint.mulesoft.com/api/v3/maven/exchange/YOUR_ORG_ID/ASSET_ID/VERSION
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  32.638 s
[INFO] Finished at: 2020-09-23T12:15:30-03:00
[INFO] ------------------------------------------------------------------------
```
