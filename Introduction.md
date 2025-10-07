## Introduction

APIs (Application Programming Interfaces) allow different software systems to communicate. In modern software architectures—mobile apps, web frontends, microservices—APIs are core.  
API testing ensures your backend endpoints behave correctly, reliably, securely.

Postman is one of the most popular tools for manual and semi-automated API testing. It gives you a friendly interface to send requests, read responses, write tests (assertions) in JavaScript, and group requests into reusable collections.

---

## Why API Testing Matters

- Early defect detection — you can test backend logic even before UI is built
- Faster feedback for developers/QA
- Integration validation — when frontend, mobile, or other services call APIs
- Reliability and stability — changes in backend should not break clients
- Security checks — verifying authentication, authorization, error handling
- Performance & load aspects (later stage)

## Core Concepts

### What is an API?

- API = Application Programming Interface  
- In web context, APIs let clients send HTTP requests (GET, POST, etc.) to a server, and get responses (often in JSON). 
- APIs define how requests are made, what data formats to use, what endpoints exist, what methods (GET, POST, etc.) and what responses are expected. 
- It's a contract: “If you send me X request, I'll respond with Y data or error.”

## Why do we need APIs?

Here are the main reasons:

1. Reusability & Faster Development

Developers don’t need to build every feature from scratch. If a service already exposes an API for some functionality (e.g. payment, maps, authentication), you can reuse it. 
- This speeds up development and reduces duplication of effort. 

2. Separation of Concerns / Abstraction

The internals of how a service works can be hidden; only what’s needed is exposed. This helps security and maintainability. 
- Different teams can work independently (backend team, frontend team) using agreed APIs.

3. Scalability & Flexibility

Different clients (web, mobile, third-party) can use the same API.
If backend changes internally, API contract can stay same, so clients are unaffected.

4. Integration & Ecosystem Building

APIs allow applications to use functionalities from other applications — e.g. integrating Google Maps, using payment gateways, using social login, etc. 


This builds richer, more powerful software ecosystems.

5. Security Control

APIs allow controlled access: you can expose only specific endpoints, use authentication/authorization, and control what data is shared. 

Internal logic and data storage remains hidden.

6. Maintainability & Versioning

As software evolves, APIs allow versioning so old clients can continue using old APIs while new clients move to updated ones.

7. Efficiency in Communication

Instead of entire systems needing to share data directly (more coupling), APIs provide lightweight, well-defined interfaces.

8. Business & Strategic Benefits

Companies can open APIs to partners or third parties (e.g. “API economy”), allowing new services, monetization, wider reach. 
Improves innovation, fosters integrations, partnerships.

### Endpoint / URL

- Endpoint (or route) is the address you call. E.g. `https://api.example.com/users/2`  
- It may include **path parameters** (like `/users/{id}`) or **query parameters** (like `?page=2&limit=10`).
- It’s a combination of the base URL (domain, path prefix) and the resource path (e.g. /users/123) plus optionally query parameters.
- The client directs an HTTP method (GET, POST, PUT, DELETE) to that endpoint to perform an action.

### HTTP Methods

Common ones:

| Method | Purpose |
|--------|---------|
| GET    | Retrieve data |
| POST   | Create new resource |
| PUT    | Update entire resource |
| PATCH  | Partial update |
| DELETE | Remove resource |

1. GET

Purpose: Retrieve data from the server.
Usage: Fetching resources or data without causing any side effects.
Example: GET /users/123 – Retrieves the user with ID 123.

2. POST

Purpose: Submit data to the server to create a new resource.
Usage: Sending data to be processed, often resulting in a new resource.
Example: POST /users – Creates a new user with the provided data.

3. PUT

Purpose: Update an existing resource with new data.
Usage: Replaces the current representation of the resource with the provided data.
Example: PUT /users/123 – Updates the user with ID 123.

4. PATCH

Purpose: Apply partial modifications to a resource.
Usage: Updating specific fields of a resource without replacing the entire entity.
Example: PATCH /users/123 – Updates specific fields of the user with ID 123.

5. DELETE

Purpose: Remove a resource from the server.
Usage: Deleting a resource identified by a URL.
Example: DELETE /users/123 – Deletes the user with ID 123.

6. HEAD

Purpose: Retrieve the headers of a resource.
Usage: Similar to GET but without the response body; used to check metadata.
Example: HEAD /users/123 – Retrieves headers for the user with ID 123.

7. OPTIONS

Purpose: Describe the communication options for the target resource.
Usage: Used to determine the allowed methods and other options supported by the server.
Example: OPTIONS /users – Describes the allowed methods for the /users resource.

8. TRACE

Purpose: Perform a message loop-back test along the path to the target resource.
Usage: Used for diagnostic purposes to trace the path of a request.
Example: TRACE /users/123 – Traces the path to the user with ID 123.

9. CONNECT

Purpose: Establish a tunnel to the server identified by the target resource.
Usage: Used for establishing a network connection, often for SSL tunneling.
Example: CONNECT example.com:443 – Establishes a tunnel to example.com on port 443

### Request vs Response

**Request** typically includes:  
- URL + method  
- Headers (e.g. `Content-Type`, `Authorization`)  
- Body / payload (for POST, PUT, PATCH)  
- Query parameters or path parameters  

**Response** includes:  
- Status code (e.g. 200, 404)  
- Response headers  
- Body (often JSON)  
- Timing, size, etc.

### Status Codes

| Code | Meaning |
|------|---------|
| 200 OK | Success |
| 201 Created | Resource created |
| 204 No Content | Success, no data |
| 400 Bad Request | Invalid input |
| 401 Unauthorized | Auth missing / invalid |
| 403 Forbidden | No permission |
| 404 Not Found | Resource not found |
| 500 Internal Server Error | Server side error |

### JSON Format

- JSON = JavaScript Object Notation  
- Definition:
JSON is a lightweight, text-based data interchange format that is easy for humans to read and write, and easy for machines to parse and generate.
- Characteristics:
    - Human-readable: Structured with key-value pairs, making it intuitive to understand.
    - Language-independent: While derived from JavaScript, JSON is supported by most programming languages.
    - Data types supported: Strings, numbers, booleans, null, objects, and arrays.
    - Structure: Uses objects ({}) and arrays ([]) to organize data.
    
- Example:

  ```json
  {
    "id": 3,
    "name": "Alice",
    "roles": ["admin", "user"],
    "address": {
      "city": "Hyderabad",
      "zip": "500081"
    }
  }