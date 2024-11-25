# OpenStack Resource Lister

A TypeScript-based utility for listing and exporting OpenStack resources across multiple tenants and locations. This tool authenticates with OpenStack endpoints and generates CSV reports of server instances and their configurations.

## Features

- Multi-tenant OpenStack resource listing
- Authentication token management
- CSV export of server details
- Support for multiple locations/regions
- Private key generation utility

## Prerequisites

- Node.js (v14 or higher)
- pnpm package manager
- Access to OpenStack endpoints
- Valid OpenStack credentials

## Installation

1. Clone the repository
2. Install dependencies:

    ```bash
    pnpm install
    ```

3. Copy the environment file and configure it:

    ```bash
    cp .env.example .env
    ```

## Configuration

### Environment Variables

Create a `.env` file with the following variables:

```env
username="your_username"
password="your_password"
BV_BASE_URL="https://object.bluvalt.com"
BV_TENANTS="base64_encoded_json"
```

### Tenant Configuration

The `BV_TENANTS` environment variable should contain a base64-encoded JSON string with the following structure:

```json
[
  {
    "name": "location_name",
    "base_url": "https://openstack.endpoint.url",
    "tenants": ["tenant1", "tenant2"]
  }
]
```

## Usage

### Listing OpenStack Resources

To list and export server resources:

```bash
# Development mode with auto-reload
pnpm dev

# Production build and run
pnpm build
pnpm start
```

The script will:

1. Authenticate with each configured OpenStack endpoint
2. Retrieve server details for each tenant
3. Export the data to a CSV file

### Generating Private Keys

To generate private keys for S3 access:

```bash
pnpm dev:creds
```

## Output Format

The tool exports server information in CSV format with the following fields:

- Name
- Status
- Created
- Updated
- HostId
- TenantId
- KeyName
- Image
- Flavor
- SecurityGroups
- Metadata
- Addresses

## Type Definitions

The project includes TypeScript definitions for OpenStack server resources. See `types.d.ts` for detailed type information.

## Development

### Project Structure

```bash
├── src/
│   ├── main.ts                 # Main application entry
│   └── generate_private_keys.ts # Key generation utility
├── types.d.ts                  # TypeScript definitions
├── package.json
└── .env
```

### Building

```bash
pnpm build
```

This will compile the TypeScript code using `tsup`.

### Development Mode

```bash
pnpm dev
```

Runs the application with `tsx watch` for automatic reloading during development.

## License

ISC

## Notes

- The application currently limits server queries to 100 results per request
- Authentication tokens are generated per session
- CSV files are saved in the project root directory
- Remember to handle your credentials securely and never commit the `.env` file

## Security Considerations

- Keep your `.env` file secure and never commit it to version control
- Rotate credentials regularly
- Monitor and audit key generation activities
- Ensure proper access controls on generated CSV files

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request
