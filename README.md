# Resolveit
This project provides a RESTful API for managing cases, including user authentication, case registration, viewing cases, and notifications.

🛠️ Tech Stack
Backend: Node.js + Express

Database: MongoDB (Mongoose)

Authentication: JWT (JSON Web Tokens)

API Format: JSON

🔐 Authentication
POST /api/login
Authenticates a user and returns a JWT token.

Request Body:

json
{
  "username": "omkar",
  "password": "secure123"
}
Response:

json
{
  "token": "your-jwt-token"
}
📝 Register Case
POST /api/cases
Registers a new case in the system.

Headers:

Authorization: Bearer <token>
Request Body:

json
{
  "title": "Missing Documents",
  "description": "Client reported missing paperwork."
}
Response:

json
{
  "id": "64c9f1e2a1b2c3d4e5f6g7h8",
  "title": "Missing Documents",
  "status": "open",
  "createdAt": "2025-08-01T12:00:00Z"
}
📂 View Cases
GET /api/cases
Retrieves a list of all registered cases.

Headers:

Authorization: Bearer <token>
Response:

json
[
  {
    "id": "64c9f1e2a1b2c3d4e5f6g7h8",
    "title": "Missing Documents",
    "status": "open"
  },
  {
    "id": "64c9f1e2a1b2c3d4e5f6g7h9",
    "title": "Fraud Investigation",
    "status": "closed"
  }
]
🔔 Notifications (Optional)
POST /api/notifications
Sends a notification related to a case.

Request Body:

json
{
  "caseId": "64c9f1e2a1b2c3d4e5f6g7h8",
  "message": "Your case has been updated."
}
Response:

json
{
  "status": "sent",
  "timestamp": "2025-08-01T12:30:00Z"
}
🧹 Additional Endpoints (Optional)
PUT /api/cases/:id
Updates an existing case.

Request Body:

json
{
  "status": "closed"
}
Response:

json
{
  "id": "64c9f1e2a1b2c3d4e5f6g7h8",
  "status": "closed"
}
DELETE /api/cases/:id
Deletes a case from the system.

Response:

json
{
  "message": "Case deleted successfully"
}
