## 🌐 REST API

**9. What are REST principles? What does "stateless" mean?**
REST is an architectural style for APIs based on principles like: using standard HTTP methods, resource-based URLs, and stateless communication. **Stateless** means each request from the client must contain **all the information needed** to process it — the server doesn't store any client session state between requests.
 
**10. HTTP methods — GET, POST, PUT, DELETE, PATCH?**
- `GET` — retrieve data (read-only, no body change on server).
- `POST` — create a new resource.
- `PUT` — update/replace an existing resource entirely.
- `DELETE` — remove a resource.
- `PATCH` — partially update a resource.
**11. HTTP status codes — 200, 201, 400, 401, 403, 404, 500?**
- `200 OK` — request succeeded.
- `201 Created` — resource successfully created.
- `400 Bad Request` — invalid request from the client.
- `401 Unauthorized` — authentication required/failed.
- `403 Forbidden` — authenticated but not allowed to access.
- `404 Not Found` — resource doesn't exist.
- `500 Internal Server Error` — server-side error.
**12. What is JSON format?**
JSON (JavaScript Object Notation) is a lightweight, text-based data format using key-value pairs, widely used for exchanging data between client and server.
```json
{"name": "Ali", "age": 25}
```
 
**13. How do you make an API request with `curl`?**
```bash
curl -X GET https://api.example.com/users
curl -X POST https://api.example.com/users -d '{"name":"Ali"}' -H "Content-Type: application/json"
```
 
**14. How to use Python's `requests` library?**
```python
import requests
response = requests.get("https://api.example.com/users")
print(response.status_code)
print(response.json())
```
 
**15. What is token / API key authentication?**
A method where the client includes a secret **token or key** (usually in the request header, e.g. `Authorization: Bearer <token>`) to prove its identity/permission, instead of sending a username/password each time.