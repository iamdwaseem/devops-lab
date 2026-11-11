# Experiment 9 — Postman Manual API Testing

**Aim:** Manually test REST endpoints using Postman.

Start backend:

```bash
node server.js
```

Base URL: `http://localhost:3000`

## Requests

**GET all students**
- Method: GET
- URL: `http://localhost:3000/students`
- Expected: 200 OK and student list.

**POST student**
- Method: POST
- URL: `http://localhost:3000/students`
- Body → raw → JSON:

```json
{
  "name": "Anil",
  "age": 20,
  "department": "CSE"
}
```

- Expected: 201 Created.

**PUT update**
- Method: PUT
- URL: `http://localhost:3000/students/1`
- JSON body:

```json
{
  "name": "Anil Kumar",
  "age": 21,
  "department": "CSE"
}
```

- Expected: 200 OK.

**DELETE**
- Method: DELETE
- URL: `http://localhost:3000/students/1`
- Expected: 200 OK.

**Negative test:** `GET /students/999` should return 404 if the backend implements GET-by-ID.

**Result:** CRUD APIs manually tested using Postman.

**Viva:** Postman is an API client; GET reads, POST creates, PUT replaces/updates, PATCH partially updates, DELETE removes.
