# WORK IN PROGRESS

**Welcome to this guide! This guide is all about the *Pterodactyl API* and how it works.**

## Windows Docs
(make sure you own a ptero panel)

*Things Needed:*

**API Key** - Normally located at https://panel.yourdomain.com/account/api (replace panel.yourdomain.com with your panel)

**cURL** - Probably already in Windows. If not installed, [download it here](https://curl.se/download.html).

### Server Resouces
*Grabs the server LIVE resources, such as CPU, RAM, Network, etc.*

**Request:**
```
curl -X GET "https://panel.yourdomain.com/api/client/servers/server_id_here/resources" ^
  -H "Accept: application/json" ^
  -H "Content-Type: application/json" ^
  -H "Authorization: Bearer YOUR_API_KEY" ^
  -b "pterodactyl_session=eyJpdiI6InhIVXp5ZE43WlMxUU1NQ1pyNWRFa1E9PSIsInZhbHVlIjoiQTNpcE9JV3FlcmZ6Ym9vS0dBTmxXMGtST2xyTFJvVEM5NWVWbVFJSnV6S1dwcTVGWHBhZzdjMHpkN0RNdDVkQiIsIm1hYyI6IjAxYTI5NDY1OWMzNDJlZWU2OTc3ZDYxYzIyMzlhZTFiYWY1ZjgwMjAwZjY3MDU4ZDYwMzhjOTRmYjMzNDliN2YifQ%3D%3D"
```

**Expected Response:**
```json
{
  "object": "stats",
  "attributes": {
    "current_state": "running",
    "is_suspended": false,
    "resources": {
      "memory_bytes": 9723904,
      "cpu_absolute": 80.257,
      "disk_bytes": 1538890570,
      "network_rx_bytes": 3254451,
      "network_tx_bytes": 206408,
      "uptime": 608913
    }
  }
}
```

**Response Errors:**
```json
{
    "errors": [
        {
            "code": "UnexpectedValueException",
            "status": "500",
            "detail": "An unexpected error was encountered while processing this request, please try again."
        }
    ]
}
```

**What the errors can be caused by:**
- Incorrect endpoint or method: If the API endpoint or HTTP method (GET, POST, PUT, DELETE, etc.) is wrong.
- Permissions issues: Lack of necessary permissions for the API key/token or user to perform the requested operation.
- CSRF token mismatch: This can happen when you're making requests without the correct CSRF token in place.
- Server overload or resource constraints: If the server is overloaded or running out of resources (CPU, memory, etc.), it might throw an error.
- API rate limiting: The API might be rejecting requests due to exceeding rate limits.
- API misconfiguration: Internal configuration issues on the server-side API.
- Invalid headers or missing required headers: Missing or malformed headers, such as missing Authorization tokens or incorrect Content-Type.
- Bad request body or missing parameters: If the request body or query parameters are incorrect or incomplete.
- Backend service failures: Issues with backend services like databases or external services that the API depends on.

### List Directores
*Grabs the files from the / directory, you can change the / to whatever directory you want (e.g. /config, /libraries, /logs, etc)*

**Request:**
```
curl -X GET "https://panel.yourdomain.com/api/client/servers/server_id/files/list?directory=/" ^
  -H "Accept: application/json" ^
  -H "Content-Type: application/json" ^
  -H "Authorization: Bearer api_key" ^
  -b "pterodactyl_session=eyJpdiI6InhIVXp5ZE43WlMxUU1NQ1pyNWRFa1E9PSIsInZhbHVlIjoiQTNpcE9JV3FlcmZ6Ym9vS0dBTmxXMGtST2xyTFJvVEM5NWVWbVFJSnV6S1dwcTVGWHBhZzdjMHpkN0RNdDVkQiIsIm1hYyI6IjAxYTI5NDY1OWMzNDJlZWU2OTc3ZDYxYzIyMzlhZTFiYWY1ZjgwMjAwZjY3MDU4ZDYwMzhjOTRmYjMzNDliN2YifQ%3D%3D"
```

**Expected Response:**
```json
{
  "object": "list",
  "data": [
    {
      "object": "file_object",
      "attributes": {
        "name": "tests.sh",
        "mode": "-rw-r--r--",
        "mode_bits": "644",
        "size": 0,
        "is_file": true,
        "is_symlink": false,
        "mimetype": "text/plain",
        "created_at": "2025-02-17T14:24:13+00:00",
        "modified_at": "2025-02-17T14:24:13+00:00"
      }
    },
    {
      "object": "file_object",
      "attributes": {
        "name": "test.sh",
        "mode": "-rw-r--r--",
        "mode_bits": "644",
        "size": 0,
        "is_file": true,
        "is_symlink": false,
        "mimetype": "text/plain",
        "created_at": "2025-02-17T14:24:07+00:00",
        "modified_at": "2025-02-17T14:24:07+00:00"
      }
    }
  ]
}
```

**Response Errors:**
```json
{
    "errors": [
        {
            "code": "UnexpectedValueException",
            "status": "500",
            "detail": "An unexpected error was encountered while processing this request, please try again."
        }
    ]
}
```

**What the errors can be caused by:**
- Incorrect endpoint or method: If the API endpoint or HTTP method (GET, POST, PUT, DELETE, etc.) is wrong.
- Permissions issues: Lack of necessary permissions for the API key/token or user to perform the requested operation.
- CSRF token mismatch: This can happen when you're making requests without the correct CSRF token in place.
- Server overload or resource constraints: If the server is overloaded or running out of resources (CPU, memory, etc.), it might throw an error.
- API rate limiting: The API might be rejecting requests due to exceeding rate limits.
- API misconfiguration: Internal configuration issues on the server-side API.
- Invalid headers or missing required headers: Missing or malformed headers, such as missing Authorization tokens or incorrect Content-Type.
- Bad request body or missing parameters: If the request body or query parameters are incorrect or incomplete.
- Backend service failures: Issues with backend services like databases or external services that the API depends on.

# More Guides soon! Stay tuned.
