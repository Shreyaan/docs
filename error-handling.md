---
title: Error Handling
description: 'Learn how to handle errors returned by Athena Copilot API.'
---

## Error Handling

When interacting with the Athena Copilot API, you might encounter errors that need to be handled gracefully in your application. All errors follow the same format and have status codes in the 400 to 500 range.

## Error Response Format

All error responses from the Athena Copilot API will have the following JSON structure:

```json
{
    "msg": "<string>"
}
```

### Example Error Response

Here’s an example of what an error response might look like:

```json
{
    "msg": "Invalid API key provided."
}
```

## Status Codes

The Athena Copilot API uses standard HTTP status codes to indicate the success or failure of an API request. Errors will have status codes in the 400 to 500 range.

### Common Error Codes

- **400 Bad Request:** The server could not understand the request due to invalid syntax. Example: Missing required parameters.
- **401 Unauthorized:** The client must authenticate itself to get the requested response. Example: Invalid API key.
- **403 Forbidden:** The client does not have access rights to the content. Example: Accessing a restricted resource.
- **404 Not Found:** The server can not find the requested resource. Example: Invalid endpoint.
- **500 Internal Server Error:** The server has encountered a situation it doesn't know how to handle. Example: Unexpected error on the server side.

## Handling Errors in Your Application



### TypeScript Example

Here's an example of how to handle errors when using the Athena Copilot TypeScript SDK:

```typescript
import { AthenaCopilot, APIError } from "athena-copilot";

const athenaCopilot = new AthenaCopilot({
    security: {
        username: "<YOUR_USERNAME_HERE>",
        password: "<YOUR_PASSWORD_HERE>",
    },
});

async function run() {
    try {
        const result = await athenaCopilot.brain.postBrain({});
        // Handle the result
        console.log(result);
    } catch (error) {
        if (error instanceof APIError) {
            console.error(`Error: ${error.response.msg}`);
        } else {
            console.error('Unexpected error', error);
        }
    }
}

run();
```

## Conclusion

By understanding the error response format and handling errors appropriately, you can build robust applications that gracefully handle issues when they arise. Always check the error message and status code to understand the cause of the error and take appropriate action.

For any further assistance, refer to our [support documentation](#) or contact our support team.