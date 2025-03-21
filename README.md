# n8n ConnectWise Manage Integration

> **⚠️ IMPORTANT NOTICE: This integration does not work** ⚠️
> 
> This repository contains a non-functional implementation that should not be used in production environments. It is being kept for reference purposes only.

This repository contains n8n workflow templates for integrating with the ConnectWise Manage API. These workflows were intended to provide similar functionality to the PowerShell wrapper for the ConnectWise Manage REST API, but in a visual workflow format.

## Contents

- `connectwise-workflow.json` - An n8n workflow template that can be imported into your n8n instance
- `connectwise-setup-guide.md` - Detailed documentation on how to set up and use the ConnectWise Manage API in n8n

## Features

The workflow templates include functionality for:

- Getting tickets from ConnectWise Manage with filtering
- Creating new tickets with required fields
- Updating existing tickets
- Basic error handling

## How to Use

**Note: These workflows do not work as expected and should not be used in production environments.**

If you wish to review the implementation for reference:

1. Import the workflow JSON into your n8n instance
2. Replace the placeholder values in the "Set CW API Config" node with your actual ConnectWise API credentials
3. Customize the query parameters and request bodies as needed for your specific use case

## Requirements

- n8n instance (cloud or self-hosted)
- ConnectWise Manage account with API access
- API credentials (Company ID, Public Key, Private Key, Client ID)

## Contributing

Contributions, issues, and feature requests are welcome!

## License

MIT