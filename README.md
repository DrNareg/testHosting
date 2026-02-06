# testHosting

A simple Flask web application for testing containerization and hosting.

## Features

- Simple Flask web server
- HTML homepage with styling
- Health check endpoint
- Docker support for containerization

## Local Development

### Prerequisites

- Python 3.11+
- pip

### Setup and Run

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Run the application:
```bash
python app.py
```

Or with debug mode enabled:
```bash
FLASK_DEBUG=true python app.py
```

3. Open your browser and navigate to:
- Homepage: http://localhost:5000
- Health check: http://localhost:5000/health

## Docker Usage

### Build the Docker image

```bash
docker build -t test-hosting-app .
```

### Run the container

```bash
docker run -p 5000:5000 test-hosting-app
```

Then access the application at http://localhost:5000

### Docker Compose (Optional)

Create a `docker-compose.yml` file (version field optional for modern Docker Compose):

```yaml
services:
  web:
    build: .
    ports:
      - "5000:5000"
    environment:
      - FLASK_DEBUG=false
```

Then run:

```bash
docker-compose up
```

## Project Structure

```
testHosting/
├── app.py              # Main Flask application
├── requirements.txt    # Python dependencies
├── Dockerfile         # Docker configuration
├── .dockerignore      # Docker ignore rules
├── templates/
│   └── index.html     # HTML homepage
└── README.md          # This file
```

## API Endpoints

- `GET /` - Homepage
- `GET /health` - Health check endpoint (returns JSON)