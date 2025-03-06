# ConnectWise Manage API Integration Guide for n8n

This guide will help you set up and use the ConnectWise Manage API in n8n workflows, effectively replacing the functionality provided by the PowerShell wrapper.

## Prerequisites

1. An active ConnectWise Manage account
2. API credentials (Company ID, Public Key, Private Key)
3. n8n instance (cloud or self-hosted)

## Authentication Setup

ConnectWise Manage API uses Basic Authentication with API keys. You'll need:

- Company ID
- Public Key
- Private Key
- Client ID

### How to Get API Credentials

1. In ConnectWise Manage, navigate to System > Setup Tables > API Keys
2. Create a new API Member/Integration
3. Set appropriate API access based on your needs
4. Generate Public/Private key pair

## Setting Up the n8n Workflow

### 1. Create API Configuration Node

This node stores your ConnectWise credentials and constructs the authentication header:

- Set your Company ID, Public Key, Private Key values
- Create an encoded auth header using Base64 encoding of "CompanyID+PublicKey:PrivateKey"

### 2. Common Operations

#### A. Get Tickets
```
GET https://api-na.myconnectwise.net/v4_6_release/apis/3.0/service/tickets
```

- Add query parameters like:
  - conditions (for filtering)
  - pageSize (for pagination)
  - orderBy (for sorting)

#### B. Create Ticket
```
POST https://api-na.myconnectwise.net/v4_6_release/apis/3.0/service/tickets
```

Required fields:
- summary
- board (id)
- company (id)

#### C. Update Ticket
```
PUT https://api-na.myconnectwise.net/v4_6_release/apis/3.0/service/tickets/{id}
```

Include only the fields you want to update in the JSON body.

## Advanced Usage

### Working with Custom Fields

Custom fields in ConnectWise are accessed through the `customFields` property:

```json
{
  "customFields": [
    {
      "id": 1,
      "caption": "Custom Field Name",
      "value": "Custom Field Value"
    }
  ]
}
```

### Error Handling

Add an "IF" node after API calls to check for errors:
- If status code ≥ 400, handle the error
- Otherwise, process the successful response

## Example Workflows

The accompanying n8n workflow JSON demonstrates:
1. Getting tickets that match specific conditions
2. Creating a new ticket with required fields
3. Updating an existing ticket's status

## Best Practices

1. Store credentials in n8n credentials, not directly in workflow
2. Use pagination for large data sets
3. Add rate limiting considerations (ConnectWise has API call limits)
4. Consider using webhooks for real-time updates

---

By following this guide, you can recreate all the functionality of the PowerShell wrapper in a visual, easy-to-maintain n8n workflow.