---
title: API Authentication Guide
description: 'Instructions on how to authenticate API requests using API keys'
---

## Introduction

This guide provides detailed instructions on how to authenticate your requests using API keys for accessing our services. 

## Obtaining API Keys

To get your API keys, navigate to the [API Key Settings Page](https://app.athenacopilot.ai/settings/api-key). API keys are organization-level credentials and can be used by any user within the organization. For enhanced security and management, we recommend using the organization admin user IDs for authentication.

### Steps to Obtain API Keys

<CardGroup cols={2}>
  <Card
    title="Step 1: Go to API Key Settings"
    icon="gear"
    href="https://app.athenacopilot.ai/settings/api-key"
  >
    Navigate to the API Key Settings Page.
  </Card>
  <Card
    title="Step 2: Copy the API Key"
    icon="clipboard"
  >
    Click on the clipboard icon to copy the API key.
  </Card>
  <Card
    title="Step 3: Collect Your Credentials"
    icon="key"
  >
    You will receive your User ID and API Key separately, as well as a base64 encoded string that combines them.
  </Card>
</CardGroup>

## Using API Keys

There are two primary methods to use API keys for authentication:

### Method 1: Base64 Encoded String

The most straightforward method is to use the provided base64 encoded string. This string combines your User ID and API key.

#### Steps to Use Base64 Encoded String

1. Copy the base64 encoded string from the API Key Settings Page.
2. Add the following header to your HTTP request:

   ```http
   Authorization: Basic <base64_encoded_string>
   ```

### Method 2: Separate User ID and API Key

Alternatively, you can use your User ID and API Key separately, especially useful for tools like Postman.

#### Steps to Use Separate User ID and API Key

1. Copy your User ID and API Key separately from the API Key Settings Page.
2. Combine your User ID and API Key in the format `userID:apiKey`.
3. Encode this combined string in base64 format.
4. Add the following header to your HTTP request:

   ```http
   Authorization: Basic <base64(userID:apiKey)>
   ```

## Authentication in Our Documentation Site

When prompted for a username and password on our documentation site, use the following:
- **Username:** Your User ID
- **Password:** Your API Key

## Example

Let's say your User ID is `user123` and your API Key is `key456`. Here's how you can authenticate your requests:

### Using Base64 Encoded String

If the base64 encoded string for `user123:key456` is `dXNlcjEyMzprZXk0NTY=`, your HTTP header will be:

```http
Authorization: Basic dXNlcjEyMzprZXk0NTY=
```

### Using Separate User ID and API Key

1. Combine User ID and API Key: `user123:key456`
2. Encode the string: `dXNlcjEyMzprZXk0NTY=`
3. Your HTTP header will be:

   ```http
   Authorization: Basic dXNlcjEyMzprZXk0NTY=
   ```

## Conclusion

By following the steps outlined in this guide, you can authenticate your API requests securely and efficiently. Whether using the base64 encoded string directly or combining your User ID and API Key manually, ensure your credentials are handled safely. For any further assistance, refer to our support documentation or contact our support team.