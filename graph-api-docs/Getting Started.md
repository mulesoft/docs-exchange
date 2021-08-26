The Exchange Graph API provides one endpoint that accepts POST requests, `https://anypoint.mulesoft.com/graph/api/v2/graphql`.

### Use an access token

To access your organization's private content, obtain an access token from the [Access Management portal](https://anypoint.mulesoft.com/exchange/portals/anypoint-platform/f1e97bc6-315a-4490-82a7-23abe036327a.anypoint-platform/access-management-api/).

### Send a request

The Exchange Graph API accepts POST requests. The body of the request must be in JSON with these fields:

```
{
  "query": "{{GRAPH QUERY}}", // This field contains the graph query 
  "variables": {
    "accessToken":"{{ACCESS TOKEN}}" // Send your Core Service access token (optional)
  }
}
```

For example, to get the groupId, assetId, and version of the Mule 4.x assets, execute this request:

```
curl -X POST \
  https://anypoint.mulesoft.com/graph/api/v2/graphql \
  -H 'content-type: application/json' \
  -d '{"query":"{assets(minMuleVersion:\"4.0.0\") {groupId assetId version}}"}'
```

### Use Connected Application Authentication

- Create a connected application (_App acts on its own behalf (client credentials)_) and either provide read-only access by setting the scope of _Exchange Viewer_, or provide read and write access by setting either the scope of _Exchange Administrator_ or the scope of _Exchange Contributor_.
- Copy the clientId and clientSecret of the connected application.
- Use basic authentication, defining the username as `~~~Client~~~` and the password as `clientId~?~clientSecret`.
    - Replace `clientId` with the client ID.
    - Replace `clientSecret` with the client secret.
- Send the request specifying the authorization in the variables object. Replace `ABC123` with the base64 encoding of the concatenation of the client ID and client secret: `~~~Client~~~:clientId~?~clientSecret`

```
{
  "query": "{{GRAPH QUERY}}", // This field contains the graph query 
  "variables": {
    "authorization":"Basic {{ABC123}}" // Send your Core Service access token (optional)
  }
}
```

For more information about the available ways to query the graph, see [Querying the graph](../Querying%20the%20graph/).
