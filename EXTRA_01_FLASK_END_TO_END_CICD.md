# Extra Topic 1 — End-to-End CI/CD for Flask with GitHub Actions and Docker

**Topic status:** Additional/out-of-syllabus preparation topic; concise runnable example.

## Minimal Flask app

`app.py`:

```python
from flask import Flask, jsonify
app = Flask(__name__)

@app.get("/")
def home():
    return jsonify(message="Flask CI/CD demo")

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

`requirements.txt`:

```text
flask
pytest
```

`test_app.py`:

```python
from app import app

def test_home():
    client = app.test_client()
    response = client.get("/")
    assert response.status_code == 200
    assert response.json["message"] == "Flask CI/CD demo"
```

`Dockerfile`:

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]
```

`.github/workflows/flask-ci.yml`:

```yaml
name: Flask CI

on: [push, pull_request]

jobs:
  test-and-build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: "3.12"
      - run: pip install -r requirements.txt
      - run: pytest -v
      - run: docker build -t flask-demo .
```

Run locally:

```bash
pip install -r requirements.txt
pytest -v
docker build -t flask-demo .
```

**Flow:** Commit/push → workflow starts → dependencies install → Pytest runs → Docker image builds.

**Viva:** CI validates changes continuously; CD automates delivery/deployment; pipeline is a sequence of automated stages.
