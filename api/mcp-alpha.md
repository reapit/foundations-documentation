---
description: A guide for interacting with our Platform MCP
---

# MCP (Alpha)

> Parameters, tools, resources, prompts and responses are likely to change in the future

The Foundations MCP server exposes the Reapit Foundations platform as a set of [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) tools that an AI model or agent can call directly. Instead of integrating against the Foundations REST API endpoint by endpoint, you connect a single MCP client to the server and the model is given a ready-made toolset for searching and managing appointments, properties, contacts, applicants, offers, and more.

This guide covers how a third party connects to the server, authenticates, and what tools are available.

{% hint style="warning" %}
To register for early access, please complete this [form](https://share-eu1.hsforms.com/1N_JYy9RLS9qI0X1oqTRi6w2eoxls?utm_campaign=323420401-FY26%20l%20Q3%20Q4%20Tapi%20sunset\&utm_source=hs_email\&utm_medium=email&_hsenc=p2ANqtz--UZQS-606QhCTChwNmTKbIziCqw5h3KxqUdYy_ansSt-xJNapbQ9xyEVMXbumRv_H7Wkvw)
{% endhint %}

### Endpoint

The server uses **Streamable HTTP**. There is a single endpoint:

```
https://foundations-mcp.iaas.reapit.cloud/mcp
```

All MCP traffic (initialization, tool listing, and tool calls) flows through this URL.

### Authentication

Every request must carry a valid Reapit JWT and identify the tenant it is acting for.

| Requirement             | Detail                                                                                                                                                                                                                                   |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Authorization`header   | `Bearer <jwt>` — a valid Reapit access token issued by Reapit Connect.                                                                                                                                                                   |
| Required scope          | The token's `scope` must include **`agencyCloud/mcp.access`**. A token without this scope is rejected.                                                                                                                                   |
| `reapit-customer`header | The tenant (customer) ID the request acts for, e.g. `SBOX`. **Only required for machine-to-machine (client-credentials) clients.** For user-context tokens the customer code is read from the token itself, so the header is not needed. |

Tokens are issued and verified by Reapit Connect. For how to register a client and obtain an access token, see the [Reapit Connect Documentation](reapit-connect.md).

> **The `agencyCloud/mcp.access` scope is required to access the MCP server.** A token without this scope is rejected with a `403`.

### Connecting with the MCP Inspector

MCP can be awkward to reason about in the abstract, so the quickest way to see the server working is the official [MCP Inspector](https://github.com/modelcontextprotocol/inspector). It's a local UI that lets you connect to an MCP server, browse its tools, and call them by hand.

Run it with:

```bash
npx @modelcontextprotocol/inspector
```

This opens the Inspector in your browser. Configure the connection as follows:

| Field          | Value                                           |
| -------------- | ----------------------------------------------- |
| Transport Type | **Streamable HTTP**                             |
| URL            | `https://foundations-mcp.iaas.reapit.cloud/mcp` |

Then add the required headers under the Inspector's authentication / custom headers section:

| Header            | Value                                                                                                                                  |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `Authorization`   | `Bearer <your-jwt>`                                                                                                                    |
| `reapit-customer` | `<your-tenant-id>` (e.g. `SBOX`) — _machine-to-machine clients only_                                                                   |
| `x-timezone`      | `Europe/London` (default UTC). This header is used to convert date times to the provided timezone in the formatted text stream output. |

Click **Connect**. Once connected, open the **Tools** tab and select **List Tools** to see everything the server exposes. You can select any tool, fill in its parameters, and run it to see the live response — a fast way to validate your credentials and explore the data before wiring the server into an agent.

### Server configuration

If you connect from your own MCP client rather than the Inspector, the equivalent configuration is:

```json
{
  "mcpServers": {
    "foundations": {
      "type": "streamable-http",
      "url": "https://foundations-mcp.iaas.reapit.cloud/mcp",
      "headers": {
        "Authorization": "Bearer <your-jwt>",
        "reapit-customer": "<your-tenant-id>"
      }
    }
  }
}
```

The exact shape of the configuration block varies by client, but the things it always needs are the Streamable HTTP transport, the `/mcp` URL, and the `Authorization` header. Add the `reapit-customer` header only if you authenticate as a machine-to-machine (client-credentials) client; user-context tokens carry the customer code themselves.

### Available tools

When you list tools, the server registers the following domains. Each tool name is prefixed with its domain.

#### Appointments

The richest domain — search, retrieve, create, and update appointments, plus open-house attendee management.

`appointments_search`, `appointments_get_by_id`, `appointments_create`, `appointments_update`, `appointments_get_types`, `appointments_get_followup_responses`, `appointments_list_open_house_attendees`, `appointments_create_open_house_attendee`, `appointments_update_open_house_attendee`, `appointments_delete_open_house_attendee`

#### Properties

Search and retrieve properties, get driving directions between locations, and manage appraisals and key movements.

`properties_search`, `properties_get_by_id`, `get_directions`, `properties_appraisals_list`, `properties_appraisals_get`, `properties_appraisals_create`, `properties_appraisals_update`, `properties_key_movements_list`, `properties_key_movements_create`, `properties_key_movements_check_in`

#### Configuration

Reference lookups used to interpret and populate other records.

`get_departments`, `get_property_attribute_options`, `appointments_get_types`, `appointments_get_followup_responses`, `companies_get_types`

#### Contacts

`contacts_search`, `contacts_get_by_id`, `contacts_create`, `contacts_update`

#### Applicants

`applicants_search`, `applicants_create`, `applicants_update`

#### Companies

`companies_search`

#### Offices

`offices_search`, `offices_get_by_id`

#### Negotiators

`negotiators_search`, `negotiators_get_by_id`

#### Areas

`areas_search`

#### Offers

`offers_search`

#### Landlords

`landlords_search`, `landlords_get_by_id`

#### Vendors

`vendors_search`, `vendors_get_by_id`

#### Tenancies

`tenancies_search`, `tenancies_get_by_id`

> The registered toolset may grow over time. Always use **List Tools** to get the authoritative, current set for your tenant.

### Embedded resources

Several Foundations records can be returned with related entities "embedded" — for example, an appointment returned alongside its negotiators, office, and property, rather than just their IDs.

**For now, the server applies these embeds automatically** on your behalf, so related data comes back already attached without you having to request it. This behaviour is convenient but **may change in the future**, so don't build logic that assumes a fixed, permanent set of embedded fields.

### Errors

Failures are returned as standard HTTP status codes:

| Status | Meaning                                                                                      |
| ------ | -------------------------------------------------------------------------------------------- |
| `400`  | Bad request — e.g. a client-credentials token without the required `reapit-customer` header. |
| `401`  | Unauthorized — missing, expired, or invalid token.                                           |
| `403`  | Forbidden — the token is valid but lacks the `agencyCloud/mcp.access` scope.                 |
| `502`  | Upstream verification failure (e.g. the identity provider could not be reached).             |

### Further reading

* [Model Context Protocol specification](https://modelcontextprotocol.io/)
* [MCP Inspector](https://github.com/modelcontextprotocol/inspector)
* [Reapit Connect documentation](reapit-connect.md)
