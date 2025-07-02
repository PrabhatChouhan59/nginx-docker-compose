Frontend & Backend Connection with Docker Compose
A full-stack web application demonstrating frontend-backend communication using Docker Compose. The project consists of a static frontend served by Nginx and a Node.js Express backend API, all containerized and orchestrated with Docker Compose.

🏗️ Project Structure
├── backend/
│   ├── Dockerfile
│   ├── package.json
│   └── server.js
├── frontend/
│   ├── Dockerfile
│   ├── index.html
│   ├── nginx.conf
│   └── static/
│       └── css/
│           └── style.css
└── docker-compose.yml
🚀 Features

Frontend: Static HTML/CSS/JavaScript application served by Nginx
Backend: Node.js Express API server with CORS support
Docker Compose: Multi-container orchestration with networking
Health Checks: Built-in backend health monitoring
API Proxy: Nginx proxies API requests to backend service
Interactive UI: Form submission and data fetching from backend

🛠️ Technologies Used
Frontend

HTML5, CSS3, JavaScript (Vanilla)
Nginx Alpine for serving static content
Responsive design

Backend

Node.js 18 (Alpine)
Express.js framework
CORS middleware
RESTful API design

DevOps

Docker & Docker Compose
Container networking
Health checks

📋 Prerequisites

Docker (version 20.0 or higher)
Docker Compose (version 3.8 or higher)
Git (for cloning the repository)

🚀 Quick Start

Clone the repository
git clone <your-repository-url>
cd <project-directory>

Build and run with Docker Compose
docker-compose up --build

Access the application

Frontend: http://localhost
Backend API: http://localhost:3001
Health Check: http://localhost:3001/api/health



📡 API Endpoints
Health Check

GET /api/health

Returns server status and timestamp
Used for container health checks



Data Operations

GET /api/data

Returns sample data array
No authentication required


POST /api/data

Accepts JSON data with name and description fields
Returns confirmation with received data



Example API Responses
GET /api/health
json{
  "status": "OK",
  "message": "Backend server is running",
  "timestamp": "2024-12-07T10:30:00.000Z"
}
GET /api/data
json{
  "message": "Hello from Backend!",
  "data": [
    { "id": 1, "name": "Item 1", "description": "First item" },
    { "id": 2, "name": "Item 2", "description": "Second item" },
    { "id": 3, "name": "Item 3", "description": "Third item" }
  ]
}
🐳 Docker Configuration
Services
Frontend Service

Container: frontend-service
Port: 80 (host) → 80 (container)
Base Image: nginx:alpine
Features: Static file serving, API proxy, CORS headers

Backend Service

Container: backend-service
Port: 3001 (host) → 3001 (container)
Base Image: node:18-alpine
Features: Express API, health checks, CORS support

Networking

Custom bridge network (app-network)
Internal service communication via container names
Frontend proxy requests to http://backend:3001

🔧 Development
Running in Development Mode

Start services
docker-compose up

View logs
docker-compose logs -f

Stop services
docker-compose down


Making Changes
Frontend Changes:

Modify files in frontend/ directory
Rebuild frontend service: docker-compose up --build frontend

Backend Changes:

Modify files in backend/ directory
Rebuild backend service: docker-compose up --build backend

Adding Dependencies
Backend Dependencies:

Update backend/package.json
Rebuild the backend service

🐛 Troubleshooting
Common Issues
Backend Not Accessible

Check if backend container is running: docker-compose ps
Verify health check: curl http://localhost:3001/api/health
Check backend logs: docker-compose logs backend

Frontend Not Loading

Ensure port 80 is not in use by other services
Check nginx configuration in frontend/nginx.conf
Verify frontend logs: docker-compose logs frontend

Useful Commands

# View running containers
docker-compose ps

# Access container shell
docker-compose exec backend sh
docker-compose exec frontend sh

# View logs
docker-compose logs -f [service-name]

# Rebuild specific service
docker-compose up --build [service-name]

# Clean up containers and networks
docker-compose down --volumes --remove-orphans
🔐 Environment Variables
Backend Environment Variables

NODE_ENV: Set to production (default in docker-compose.yml)
PORT: Backend port (default: 3001)

Customizing Environment
Create a .env file in the project root:
envBACKEND_PORT=3001
FRONTEND_PORT=80
NODE_ENV=production
📊 Health Monitoring
The backend service includes built-in health checks:

Endpoint: /api/health
Interval: 30 seconds
Timeout: 10 seconds
Retries: 3 attempts
Start Period: 40 seconds

🚀 Production Deployment
For production deployment:

Security: Update CORS origins in backend/server.js
Environment: Set appropriate environment variables
Reverse Proxy: Consider using a reverse proxy (Traefik, nginx)
SSL: Add HTTPS certificates
Monitoring: Implement proper logging and monitoring
