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


For more information about the available ways to query the graph, see [Querying the graph](../Querying%20the%20graph/).
