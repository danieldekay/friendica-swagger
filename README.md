# Friendica OpenAPI Specification

A comprehensive OpenAPI 3.0 specification for the Friendica API, providing detailed documentation for all available endpoints, request/response schemas, and authentication methods.

## What is Friendica?

[Friendica](https://friendi.ca/) is a decentralized social network platform that enables users to connect and communicate across different social media networks. It's part of the fediverse and supports multiple protocols including ActivityPub, Diaspora, and OStatus, allowing users to interact with other decentralized platforms like Mastodon, Hubzilla, and more.

## About This Repository

This repository contains the OpenAPI 3.0 specification for the Friendica API, which provides comprehensive documentation for:

- **Social Media Functionality**: Status updates, timelines, conversations
- **Direct Messaging**: Private messaging between users
- **Media Management**: Photo upload, album management, and media attachments
- **User Management**: Profiles, contacts, and user information
- **Groups**: Creating, updating, and managing user groups
- **Events**: Event creation and management
- **Notifications**: Notification management and preferences
- **Authentication**: OAuth 1.0a and HTTP Basic Authentication

## Features

The API specification covers the following major areas:

### Core Social Features
- Public and network timelines
- Status posting and replies
- Conversation management
- User mentions and hashtags

### Direct Messaging
- Send and receive private messages
- Message conversation threads
- Message search functionality
- Message status management

### Media & Photos
- Photo upload and management
- Album creation and organization
- Image scaling and metadata
- Access control for media

### User & Profile Management
- User profile information
- Contact management
- Profile customization
- External profile lookup

### Groups & Communities
- Group creation and management
- Member management
- Group-specific permissions

### Notifications
- Real-time notifications
- Notification preferences
- Read/unread status management

## Getting Started

### Prerequisites

- **For API Integration**: A Friendica server instance
- **For Documentation**: Any OpenAPI 3.0 compatible tool
- **For Development**: Node.js, Python, or Docker (depending on your preferred toolset)

### Using the OpenAPI Specification

#### 1. View API Documentation

You can use various tools to generate and view the API documentation:

**Using Swagger UI (Online)**:
1. Go to [Swagger Editor](https://editor.swagger.io/)
2. Copy the contents of `openapi.yaml` and paste it into the editor
3. View the rendered documentation in the right panel

**Using Docker**:
```bash
# Serve the documentation locally
docker run -p 8080:8080 -e SWAGGER_JSON=/openapi.yaml -v $(pwd):/usr/share/nginx/html/openapi.yaml swaggerapi/swagger-ui
```

**Using Node.js tools**:
```bash
# Install redoc-cli globally
npm install -g redoc-cli

# Generate static HTML documentation
redoc-cli build openapi.yaml --output friendica-api-docs.html
```

#### 2. Generate Client SDKs

You can generate client SDKs in various programming languages:

**Using OpenAPI Generator**:
```bash
# Install OpenAPI Generator
npm install -g @openapitools/openapi-generator-cli

# Generate Python client
openapi-generator-cli generate -i openapi.yaml -g python -o ./python-client

# Generate JavaScript client
openapi-generator-cli generate -i openapi.yaml -g javascript -o ./js-client

# Generate Java client
openapi-generator-cli generate -i openapi.yaml -g java -o ./java-client
```

#### 3. Validate the Specification

```bash
# Install spectral for linting
npm install -g @stoplight/spectral-cli

# Validate the OpenAPI spec
spectral lint --ruleset spectral:oas openapi.yaml
```

## API Authentication

The Friendica API supports two authentication methods:

### 1. HTTP Basic Authentication
```bash
curl -u username:password https://your-friendica-instance.com/api/statuses/public_timeline
```

### 2. OAuth 1.0a
The API supports OAuth 1.0a authentication. Refer to the [Friendica OAuth documentation](https://wiki.friendi.ca/docs/api-authentication#oauth-1-0a) for implementation details.

**Note**: OpenAPI 3.0 has limited support for OAuth 1.0a specification, so refer to the Friendica documentation for complete OAuth implementation details.

## Example Usage

### Fetching Public Timeline
```bash
curl -X GET "https://demo.friendi.ca/api/statuses/public_timeline?count=10" \
     -H "accept: application/json"
```

### Creating a Status Update (requires authentication)
```bash
curl -X POST "https://your-instance.com/api/statuses/update" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -H "Authorization: Basic <base64-encoded-credentials>" \
     -d "status=Hello, Friendica!"
```

### Retrieving User Notifications (requires authentication)
```bash
curl -X GET "https://your-instance.com/api/friendica/notifications" \
     -H "accept: application/json" \
     -H "Authorization: Basic <base64-encoded-credentials>"
```

## Server Configuration

The API base URL follows this pattern:
```
https://{host}/api
```

Where `{host}` is your Friendica server domain. The default example uses `demo.friendi.ca`.

## Development

### Contributing

1. Fork this repository
2. Make your changes to the `openapi.yaml` file
3. Validate your changes:
   ```bash
   # Check YAML syntax
   python3 -c "import yaml; yaml.safe_load(open('openapi.yaml'))"
   
   # Lint with spectral (if available)
   spectral lint --ruleset spectral:oas openapi.yaml
   ```
4. Submit a pull request with a clear description of your changes

### File Structure

```
friendica-swagger/
├── openapi.yaml          # Main OpenAPI 3.0 specification
└── README.md            # This documentation file
```

### Updating the Specification

When updating the OpenAPI specification:

1. Ensure all new endpoints include proper examples
2. Add appropriate error responses (400, 403, 404, 500)
3. Document required vs optional parameters
4. Include security requirements for protected endpoints
5. Test against a real Friendica instance when possible

## Related Resources

- **Friendica Official Website**: https://friendi.ca/
- **Friendica API Documentation**: https://wiki.friendi.ca/docs/api
- **Friendica Source Code**: https://github.com/friendica/friendica
- **OpenAPI Specification**: https://spec.openapis.org/oas/v3.0.0
- **Swagger Tools**: https://swagger.io/tools/
- **OpenAPI Generator**: https://openapi-generator.tech/

## API Coverage

This specification aims to document the complete Friendica API. Currently covered endpoints include:

- **Twitter-compatible API**: Most endpoints that provide compatibility with Twitter API clients
- **Friendica-specific API**: Extended functionality unique to Friendica
- **GNU Social/StatusNet compatibility**: Legacy endpoints for compatibility
- **Mastodon API compatibility**: Selected endpoints for Mastodon client compatibility

## License

This OpenAPI specification is provided for documentation purposes. Please refer to the [Friendica project](https://github.com/friendica/friendica) for the actual software license.

## Support

For questions about this OpenAPI specification:
- Open an issue in this repository
- Refer to the [Friendica API documentation](https://wiki.friendi.ca/docs/api)
- Join the Friendica community forums

For questions about Friendica itself:
- Visit the [Friendica support forums](https://forum.friendi.ca/)
- Check the [Friendica wiki](https://wiki.friendi.ca/)