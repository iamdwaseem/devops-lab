# Experiment 1 — Simple Backend Project: CRUD REST APIs

**Aim:** Build a student-management backend with GET, POST, PUT and DELETE APIs.

## Setup

```bash
mkdir student-api
cd student-api
npm init -y
npm install express
```

## `server.js`

```javascript
const express = require('express');
const app = express();
app.use(express.json());

let students = [
  { id: 1, name: 'Rahul', age: 20, department: 'CSE' },
  { id: 2, name: 'Priya', age: 21, department: 'CSE' }
];

app.get('/students', (req, res) => res.json(students));

app.post('/students', (req, res) => {
  const student = { id: students.length + 1, ...req.body };
  students.push(student);
  res.status(201).json(student);
});

app.put('/students/:id', (req, res) => {
  const id = Number(req.params.id);
  const index = students.findIndex(s => s.id === id);
  if (index === -1) return res.status(404).json({ message: 'Not found' });
  students[index] = { id, ...req.body };
  res.json(students[index]);
});

app.delete('/students/:id', (req, res) => {
  const id = Number(req.params.id);
  const index = students.findIndex(s => s.id === id);
  if (index === -1) return res.status(404).json({ message: 'Not found' });
  students.splice(index, 1);
  res.json({ message: 'Deleted successfully' });
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

## Run and test

```bash
node server.js
```

Use Postman or REST Client:
- `GET http://localhost:3000/students` → 200
- `POST http://localhost:3000/students` with JSON body → 201
- `PUT http://localhost:3000/students/1` with updated JSON → 200
- `DELETE http://localhost:3000/students/2` → 200
- `GET /students/999` is not implemented in this minimal version; use the later record's GET-by-ID implementation if required.

**Result:** CRUD REST endpoints are implemented using Express.

**Viva:** CRUD = Create, Read, Update, Delete. REST uses HTTP methods to operate on resources. Express is a Node.js web framework. `express.json()` parses JSON request bodies.
