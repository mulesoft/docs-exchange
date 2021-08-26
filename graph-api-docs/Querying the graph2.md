The Exchange Graph API provides two root elements called `assets` and `asset`.
The `assets` element can be used to search assets in Exchange using multiple criteria.
The `asset` element can be used to obtain detailed information about a specific asset, and related platform entities, by providing at least the groupId and assetId.

All the arguments for the root elements and the response schemas can be explored in the [GraphiQL graphical interface](https://anypoint.mulesoft.com/graph/api/v2/graphql).

### Search for assets using the `assets` element

Build a search query by specifying different arguments within the `assets` element. The available arguments are:

- **organizationIds ([String])**: A list of organization IDs to filter by. This enables asking for assets belonging to specific business groups.
- **public (Boolean)**: Fetch only assets that are publicly shared.
- **categories ([CategorySearchField])**: Fetch assets that have these categories. Example: `categories:{key:"industry"}`
- **customFields (CustomSearchFields)** Fetch assets that have these custom fields. Example: `customFields:{textCustomField:{key:"api"}}`
- **masterOrganizationId (String)**: This enables asking for assets belonging to a specific master organization ID.
- **searchTerm (String)**: Use this field for free text searches.
- **types ([String])**: A list of types to filter by. Examples: `template`, `example`, `rest-api`, `soap-api`
- **offset (Int)**: Pagination control. The number of assets to skip when returning the result. Defaults to 0.
- **limit (Int)**: Pagination control. The number of assets to return in one page. Defaults to 20.
- **minMuleVersion (String)**: Fetch assets that have this `minMuleVersion`.
- **isGenerated (Boolean)**: Fetch only assets that were auto-generated as a `connector` or `extension`.
- **extensionModel (ExtensionModelInput)**: Fetch assets that have these extension models. Example: `extensionModel:{hasOperations:true}`
- **labels ([String])**: Fetch assets that have these labels. Example: `labels: ["mulesoft-certified"]`
- **latestVersionsOnly (Boolean)**: Fetch only the assets' latest versions.
- **sharedWithMe (Boolean)**:  Fetch only assets shared with my user account.

#### Example requests to search using the graph

- Return the third 10 item page of Mule 4.0.0 extensions for the MuleSoft organization.

```
curl -X POST \
  https://anypoint.mulesoft.com/graph/api/v2/graphql \
  -H 'content-type: application/json' \
  -d '{"query":"{assets(organizationIds: [\"68ef9520-24e9-4cf2-b2f5-620025690913\"], minMuleVersion: \"4.0.0\", types: [\"extension\"], offset: 20, limit: 10) {groupId assetId version}}"}'
```

- Return the first 5 item page of REST APIs with Product API version named `v1`.

```
curl -X POST \
  https://anypoint.mulesoft.com/graph/api/v2/graphql \
  -H 'content-type: application/json' \
  -d '{"query":"{assets(types: [\"rest-api\"], offset: 0, limit: 5, latestVersionsOnly: true) {groupId assetId version}}"}'
```

### Get a particular asset using the `asset` element

If you know the groupId, assetId, and/or version (GAV) of an asset, you can access it using the `asset` element. The available arguments are:

- **organizationId (String)**: The organization ID of the asset's organization.
- **groupId (String)**: The group ID of the asset to retrieve.
- **assetId (String)**: The asset ID of the asset to retrieve.
- **version (String)**: The version of the asset to retrieve.
- **versionGroup (String)**: The version group of the asset to retrieve.
- **public (Boolean)**: Fetch only assets that were publicly shared.


#### Example requests to retrieve an asset using the graph

- Returns the asset with the specified GAV.

```
curl -X POST \
  https://anypoint.mulesoft.com/graph/api/v2/graphql \
  -H 'content-type: application/json' \
  -d '{"query":"{asset(groupId: \"org.mule.connectors\",assetId: \"mule-db-connector\",version: \"1.2.1\"){groupId assetId version}}"}'
```

- Returns all the versions of an asset given its `groupId` and `assetId`.

```
curl -X POST \
  https://anypoint.mulesoft.com/graph/api/v2/graphql \
  -H 'content-type: application/json' \
  -d '{"query":"{asset(groupId: \"org.mule.connectors\",assetId: \"mule-db-connector\"){groupId assetId otherVersions { version }}}"}'
```
