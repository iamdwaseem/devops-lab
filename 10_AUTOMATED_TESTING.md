# Experiment 10 — Automated Testing of APIs

**Aim:** Create automated test cases for REST APIs.

## A. Uploaded record variant: Node.js built-in fetch + assert

Start the backend first. Create `test_cases.js`:

```javascript
const assert = require('node:assert/strict');
const BASE_URL = 'http://localhost:3000';

async function runTests() {
  let temporaryStudentId;

  const getResponse = await fetch(`${BASE_URL}/students`);
  const getBody = await getResponse.json();
  assert.equal(getResponse.status, 200);
  console.log('PASS: GET /students returns 200');

  assert.ok(Array.isArray(getBody.data));
  console.log('PASS: GET response contains student data');

  const postResponse = await fetch(`${BASE_URL}/students`, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      name: 'Temporary Test Student',
      rollNo: 'TEST001',
      course: 'Testing'
    })
  });
  const postBody = await postResponse.json();
  assert.equal(postResponse.status, 201);
  temporaryStudentId = postBody.data.id;
  console.log('PASS: POST creates student');

  const patchResponse = await fetch(`${BASE_URL}/students/${temporaryStudentId}`, {
    method: 'PATCH',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ course: 'Updated Testing' })
  });
  assert.equal(patchResponse.status, 200);
  console.log('PASS: PATCH updates student');

  const deleteResponse = await fetch(`${BASE_URL}/students/${temporaryStudentId}`, {
    method: 'DELETE'
  });
  assert.equal(deleteResponse.status, 200);
  console.log('PASS: DELETE removes student');

  console.log('All API test cases passed.');
}

runTests().catch(error => {
  console.error('TEST FAILED:', error);
  process.exitCode = 1;
});
```

Run:

```bash
node test_cases.js
```

Expected: PASS messages for GET, POST, PATCH and DELETE.

## B. Pytest quick example (Python)

`calculator.py`:

```python
def add(a, b):
    return a + b
```

`test_calculator.py`:

```python
from calculator import add

def test_add():
    assert add(2, 3) == 5
```

Run:

```bash
pip install pytest
pytest -v
```

Expected: `1 passed`.

## C. JUnit quick example (Java)

`Calculator.java`:

```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

`CalculatorTest.java` (JUnit 5):

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class CalculatorTest {
    @Test
    void testAdd() {
        Calculator calculator = new Calculator();
        assertEquals(5, calculator.add(2, 3));
    }
}
```

Run in a Maven project with JUnit 5 dependency:

```bash
mvn test
```

**Result:** Automated tests verify expected behavior and report pass/fail.

**Viva:** Test case = input/condition plus expected result; assertion = comparison; Pytest = Python framework; JUnit = Java framework; Jest = JavaScript framework; Supertest = HTTP testing library for Node.js.
