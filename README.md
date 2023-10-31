## Redis Data API Documentation

### Base Startup Sequence

```
redis-server
./init_redis_data.sh
```

### 1. **Retrieve Data (`GET`)**

#### Endpoint: `/data/{key}`

**Description:** Retrieve the value associated with the specified key from Redis.

**HTTP Method:** `GET`

**Parameters:**
- `{key}` (path parameter) - The key of the data to retrieve from Redis.

**Response:**
- **200 OK**
  - Content Type: `application/json`
  - Body: JSON object containing the retrieved data.

  Example:
  ```json
  {
    "key": "example_key",
    "value": "example_value"
  }
  ```

- **404 Not Found**
  - Content Type: `application/json`
  - Body: JSON object indicating the key was not found.

  Example:
  ```json
  {
    "error": "Key not found"
  }
  ```

**Example Request:**
```
GET https://api.example.com/redis/data/example_key
```

### 2. **Store Data (`POST`)**

#### Endpoint: `/data`

**Description:** Store data in Redis with the specified key-value pair.

**HTTP Method:** `POST`

**Parameters:**
- `key` (query parameter) - The key under which the data will be stored in Redis.
- `value` (query parameter) - The value associated with the key.

**Response:**
- **201 Created**
  - Content Type: `application/json`
  - Body: JSON object confirming the data was successfully stored.

  Example:
  ```json
  {
    "message": "Data stored successfully",
    "key": "example_key",
    "value": "example_value"
  }
  ```

- **400 Bad Request**
  - Content Type: `application/json`
  - Body: JSON object indicating a validation error or malformed request.

  Example:
  ```json
  {
    "error": "Invalid request format"
  }
  ```

**Example Request:**
```
POST https://api.example.com/redis/data?key=example_key&value=example_value
```

### 3. **Update Data (`PUT`)**

#### Endpoint: `/data/{key}`

**Description:** Update the value associated with the specified key in Redis.

**HTTP Method:** `PUT`

**Parameters:**
- `{key}` (path parameter) - The key of the data to be updated in Redis.
- `value` (query parameter) - The new value to associate with the key.

**Response:**
- **200 OK**
  - Content Type: `application/json`
  - Body: JSON object confirming the data was successfully updated.

  Example:
  ```json
  {
    "message": "Data updated successfully",
    "key": "example_key",
    "value": "new_example_value"
  }
  ```

- **404 Not Found**
  - Content Type: `application/json`
  - Body: JSON object indicating the key was not found.

  Example:
  ```json
  {
    "error": "Key not found"
  }
  ```

**Example Request:**
```
PUT https://api.example.com/redis/data/example_key?value=new_example_value
```

### 4. **Delete Data (`DELETE`)**

#### Endpoint: `/data/{key}`

**Description:** Delete the data associated with the specified key from Redis.

**HTTP Method:** `DELETE`

**Parameters:**
- `{key}` (path parameter) - The key of the data to be deleted from Redis.

**Response:**
- **204 No Content**
  - Content Type: N/A
  - Body: N/A

- **404 Not Found**
  - Content Type: `application/json`
  - Body: JSON object indicating the key was not found.

  Example:
  ```json
  {
    "error": "Key not found"
  }
  ```

**Example Request:**
```
DELETE https://api.example.com/redis/data/example_key
```

---
