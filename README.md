# Friendica API

## Description
OpenAPI specification for the Friendica API, generated using https://jules.google.com.

## API Documentation
The full API specification, detailing all endpoints, request/response schemas, and parameters, can be found in the [openapi.yaml](openapi.yaml) file in this repository.

## Authentication
This API supports the following authentication methods:

### Basic Authentication
HTTP Basic Authentication can be used for API requests.

### OAuth 1.0a
Friendica uses OAuth 1.0a for authentication. For detailed implementation information, please refer to the [Friendica OAuth 1.0a documentation](https://wiki.friendi.ca/docs/api-authentication#oauth-1-0a).

## Endpoints
The Friendica API provides a wide range of endpoints to interact with social data. Some of the key functionalities include:

*   **Statuses:** Fetching public timelines, user replies, and conversations (e.g., `/statuses/public_timeline`, `/conversation/show`).
*   **Direct Messages:** Managing direct messages (e.g., `/direct_messages/all`, `/direct_messages/new`).
*   **User Accounts:** Verifying credentials and updating profiles (e.g., `/account/verify_credentials`, `/account/update_profile`).
*   **Photos & Albums:** Managing user photos and photo albums (e.g., `/friendica/photos/list`, `/friendica/photo/create`).
*   **Notifications:** Retrieving user notifications (e.g., `/friendica/notifications`).
*   **Events:** Listing user events (e.g., `/friendica/events`).

For a complete list of endpoints and their detailed specifications, please refer to the [openapi.yaml](openapi.yaml) file.

## Contributing
Contributions to this project are welcome!

If you would like to contribute, please follow these general guidelines:
1.  Check the issue tracker for existing bugs or feature requests.
2.  Fork the repository and create a new branch for your changes.
3.  Ensure your code adheres to any existing style guidelines.
4.  Write tests for your changes, if applicable.
5.  Submit a pull request with a clear description of your changes.

## License
This project is licensed under the AGPL-3.0 License. See the [LICENSE.md](LICENSE.md) file for details.
