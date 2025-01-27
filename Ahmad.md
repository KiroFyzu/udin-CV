
# YouTube Downloader API Proxy

This project provides a proxy endpoint for downloading YouTube videos or audio by interacting with the external API `https://api.ahmmikun.live/api/downloader/ytdl`.

## Features
- Accepts a YouTube video URL and desired file type (`mp3`, `mp4`) as input.
- Forwards the request to the external API and returns the response to the client.
- Validates query parameters for better error handling.

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo-name.git
   cd your-repo-name
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the server:
   ```bash
   node index.js
   ```

4. The server runs by default on `http://localhost:3000`.

---

## API Documentation

### **Endpoint Overview**

#### **URL:**  
```
GET /api/download
```

#### **Query Parameters**

| Parameter | Type   | Required | Description                                          |
|-----------|--------|----------|------------------------------------------------------|
| `url`     | String | Yes      | The YouTube video URL to be downloaded.             |
| `type`    | String | Yes      | The desired file format, e.g., `mp3` or `mp4`.      |

---

### **Request Example**

```http
GET /api/download?url=https://www.youtube.com/watch?v=dQw4w9WgXcQ&type=mp3
```

---

### **Response**

#### **Success Response**

**Status Code:** `200 OK`  
**Content:**
```json
{
  "status": "success",
  "data": {
    "download_url": "https://example.com/download.mp3",
    "filename": "video.mp3",
    "type": "mp3"
  }
}
```

#### **Error Responses**

- **Missing Query Parameters**  
  **Status Code:** `400 Bad Request`  
  **Content:**
  ```json
  {
    "message": "Parameter 'url' and 'type' are required."
  }
  ```

- **Internal Server Error**  
  **Status Code:** `500 Internal Server Error`  
  **Content:**
  ```json
  {
    "message": "An error occurred while processing the request.",
    "error": "Detailed error message"
  }
  ```

---

### **Error Handling**

1. **400 - Bad Request:**  
   Returned if `url` or `type` is not provided in the query parameters.

2. **500 - Internal Server Error:**  
   Returned if an error occurs while processing the request to the external API.

---

## Usage Notes

1. Ensure the `url` parameter is a valid YouTube video link.
2. Supported `type` values depend on the external API. Common values include `mp3` and `mp4`.
3. This endpoint acts as a proxy, so any errors from the external API will be propagated to the client.

---

## Dependencies

- **Express**: Web framework for Node.js.
- **Axios**: HTTP client for making requests to the external API.

Install the required packages:
```bash
npm install express axios
```

---

## Development

1. Fork and clone the repository.
2. Make your changes and test locally.
3. Submit a pull request for review.

---

## License

This project is open source and available under the [Without License](LICENSE)
