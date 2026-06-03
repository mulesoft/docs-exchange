# Scanner Setup Guides

## Adding a Scanner for Anthropic Claude Managed Agents

Add a scanner to discover, import, and sync agents from Claude Managed Agents into Exchange. Then you can govern the agents and consume them in other applications.

### Before You Begin

Before adding the scanner, verify that you have the permission, context, and these Anthropic Claude credentials:

- Exchange Administrator permission
- Paid Anthropic account
- Claude API key

### Add a Scanner for Anthropic Claude Managed Agents

1. Verify that you are in the business group where you want to add the scanner.
2. From the sidebar in Exchange, click **Scanners**.
3. Enter a name for the scanner.
4. From **Scanner Run Configuration**, complete these fields or options:

| **Field/Option** | **Value** |
|---|---|
| **Run Schedule** | Select a frequency and time. |
| **Sync Review** | Select an option: **Auto-resolve** or **Ask to review**. |

5. From **Connection Configuration**, complete these fields:

| **Field** | **Value** |
|---|---|
| **Provider** | Select **Anthropic**. |
| **Platform** | Select **Anthropic Claude**. |
| **Service Type** | **Agents** selected by default. |
| **Authentication Method** | Select **Access Keys**. |
| **API Key** | Enter the API key. |

6. Click **Test Connection**.

If the connection fails, review the **Connection Configuration** settings. Update the settings, and then test the connection again.

7. To send email notifications:
   - Select **Advanced Settings** and turn on **Send Email Notifications**.
   - Enter an email address.
8. Click **Add Scanner**.

---

## Adding a Scanner for Databricks Unity Catalog

Add a scanner to discover, import, and sync agents from Databricks Unity Catalog into Exchange. Then you can govern the agents and consume them in other applications.

### Before You Begin

Before adding the scanner, verify that you have the permission, context, and these credentials:

- Exchange Administrator permission
- Workspace URL
- Databricks client ID
- Databricks client secret
- Service principal permission requirements on each serving endpoint

Use the Databricks Permissions API:

```json
PATCH /api/2.0/permissions/serving-endpoints/{endpoint_id}
{
  "access_control_list": [
    {
      "service_principal_name": "<clientId>",
      "permission_level": "CAN_QUERY"
    }
  ]
}
```

| API Endpoint | Required Permission |
|---|---|
| GET /api/2.0/serving-endpoints | CAN_VIEW or higher |
| GET /api/2.0/serving-endpoints/{name} | CAN_VIEW or higher |
| GET /api/2.0/serving-endpoints/{name}/openapi | CAN_VIEW or higher |
| POST /serving-endpoints/{name}/invocations | CAN_QUERY or higher |

### Add a Scanner for Databricks Unity Catalog

1. Verify that you are in the business group where you want to add the scanner.
2. From the sidebar in Exchange, click **Scanners**.
3. Enter a name for the scanner.
4. From **Scanner Run Configuration**, complete these fields or options:

| **Field/Option** | **Value** |
|---|---|
| **Run Schedule** | Select a frequency and time. |
| **Sync Review** | Select an option: **Auto-resolve** or **Ask to review**. |

5. From **Connection Configuration**, complete these fields:

| **Field** | **Value** |
|---|---|
| **Provider** | Select **Databricks**. |
| **Platform** | Select **Agent Bricks**. |
| **Service Type** | **Agents** selected by default. |
| **Authentication Method** | **OAuth** selected by default. |
| **Workspace URL** | Enter the workspace URL. |
| **Client ID** | Enter the client ID. |
| **Client Secret** | Enter the client secret. |

6. Click **Test Connection**.

If the connection fails, review the **Connection Configuration** settings. Update the settings, and then test the connection again.

7. To send email notifications:
   - Select **Advanced Settings** and turn on **Send Email Notifications**.
   - Enter an email address.
8. Click **Add Scanner**.

---

## Adding a Scanner for Snowflake MCP Server

Add a scanner to discover, import, and sync MCP servers from Snowflake into Exchange. Then you can govern the servers and consume them in other applications.

### Before You Begin

Before adding the scanner, verify that you have the permission, context, and these Snowflake MCP credentials:

- Exchange Administrator permission
- Snowflake ACCOUNTADMIN role permission
- Snowflake Enterprise edition account with MCP servers enabled
- Snowflake account URL
- Snowflake programmatic access token (PAT)

### Add a Scanner for Snowflake MCP

1. Verify that you are in the business group where you want to add the scanner.
2. From the sidebar in Exchange, click **Scanners**.
3. Enter a name for the scanner.
4. From **Scanner Run Configuration**, complete these fields or options:

| **Field/Option** | **Value** |
|---|---|
| **Run Schedule** | Select a frequency and time. |
| **Sync Review** | Select an option: **Auto-resolve** or **Ask to review**. |

5. From **Connection Configuration**, complete these fields:

| **Field** | **Value** |
|---|---|
| **Provider** | Select **Snowflake**. |
| **Platform** | Select **Cortex AI**. |
| **Service Type** | Select **MCPs**. |
| **Authentication Method** | **Service Account** selected by default. |
| **Account URL** | Enter the Snowflake account URL. |
| **Programmatic Access Token** | Enter the programmatic access token. |
| **Database Filter** | Enter one database name or a comma-separated list. |
| **Schema Filter** | Enter one schema name or a comma-separated list. |

6. Click **Test Connection**.

If the connection fails, review the **Connection Configuration** settings. Update the settings, and then test the connection again.

7. To send email notifications:
   - Select **Advanced Settings** and turn on **Send Email Notifications**.
   - Enter an email address.
8. Click **Add Scanner**.

---

## Adding a Scanner for Snowflake Cortex AI

Add a scanner to discover, import, and sync agents from Snowflake Cortex AI into Exchange. Then you can govern the agents and consume them in other applications.

### Before You Begin

Before adding the scanner, verify that you have the permission, context, and these Snowflake Cortex AI credentials:

- Exchange Administrator permission
- Snowflake Enterprise edition account with Cortex agents enabled
- Snowflake ACCOUNTADMIN role permission
- Snowflake account URL
- Snowflake programmatic access token (PAT)

### Add a Scanner for Snowflake Cortex AI

1. Verify that you are in the business group where you want to add the scanner.
2. From the sidebar in Exchange, click **Scanners**.
3. Enter a name for the scanner.
4. From **Scanner Run Configuration**, complete these fields or options:

| **Field/Option** | **Value** |
|---|---|
| **Run Schedule** | Select a frequency and time. |
| **Sync Review** | Select an option: **Auto-resolve** or **Ask to review**. |

5. From **Connection Configuration**, complete these fields:

| **Field** | **Value** |
|---|---|
| **Provider** | Select **Snowflake**. |
| **Platform** | Select **Cortex AI**. |
| **Service Type** | **Agents** selected by default. |
| **Authentication Method** | **Service Account** selected by default. |
| **Account URL** | Enter the account URL. |
| **Programmatic Access Token** | Enter the programmatic access token. |
| **Database Filter** | Enter one database name or a comma-separated list. |
| **Schema Filter** | Enter one schema name or a comma-separated list. |

6. Click **Test Connection**.

If the connection fails, review the **Connection Configuration** settings. Update the settings, and then test the connection again.

7. To send email notifications:
   - Select **Advanced Settings** and turn on **Send Email Notifications**.
   - Enter an email address.
8. Click **Add Scanner**.

---

## Adding a Scanner for LangChain LangSmith

Add a scanner to discover, import, and sync agents from LangSmith into Exchange. Then you can govern the agents and consume them in other applications.

### Before You Begin

Before adding the scanner, verify that you have the permission, context, and these credentials:

- Exchange Administrator permission
- Plus plan (or higher) workspace in LangSmith
- LangSmith API key for the workspace
- LangSmith workspace ID

### Add a Scanner for LangChain LangSmith

1. Verify that you are in the business group where you want to add the scanner.
2. From the sidebar in Exchange, click **Scanners**.
3. Enter a name for the scanner.
4. From **Scanner Run Configuration**, complete these fields or options:

| **Field/Option** | **Value** |
|---|---|
| **Run Schedule** | Select a frequency and time. |
| **Sync Review** | Select an option: **Auto-resolve** or **Ask to review**. |

5. From **Connection Configuration**, complete these fields:

| **Field** | **Value** |
|---|---|
| **Provider** | Select **LangChain**. |
| **Platform** | Select **LangSmith**. |
| **Service Type** | **Agents** selected by default. |
| **Authentication Method** | **Access Keys** selected by default. |
| **LangSmith API Key** | Enter the API key. |
| **Workspace ID** | Enter the workspace ID. |
| **Region** | Select the region for your workspace: US or EU. |

6. Click **Test Connection**.

If the connection fails, review the **Connection Configuration** settings. Update the settings, and then test the connection again.

7. To send email notifications:
   - Select **Advanced Settings** and turn on **Send Email Notifications**.
   - Enter an email address.
8. Click **Add Scanner**.
