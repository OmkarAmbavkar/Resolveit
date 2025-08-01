# Resolveit
## 📚 API Documentation – ResolveIt

ResolveIt provides a secure and scalable RESTful API for managing cases, user authentication, and notifications.

### 🔗 Live Swagger Docs

You can explore and test the API using Swagger UI:

### 🧩 Swagger Specification (OpenAPI 3.0)

<details>
  <summary>Click to expand full Swagger YAML</summary>

```yaml
openapi: 3.0.0
info:
  title: ResolveIt API
  version: 1.0.0
  description: API for managing cases, users, and notifications in ResolveIt.
servers:
  - url: https://resolveit.example.com
    description: Production Server
paths:
  /api/login:
    post:
      summary: User login
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                username:
                  type: string
                password:
                  type: string
              required:
                - username
                - password
      responses:
        '200':
          description: JWT token returned
          content:
            application/json:
              schema:
                type: object
                properties:
                  token:
                    type: string

  /api/cases:
    post:
      summary: Register a new case
      security:
        - bearerAuth: []
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                title:
                  type: string
                description:
                  type: string
              required:
                - title
                - description
      responses:
        '201':
          description: Case created
          content:
            application/json:
              schema:
                type: object
                properties:
                  id:
                    type: string
                  title:
                    type: string
                  status:
                    type: string
                  createdAt:
                    type: string
                    format: date-time

    get:
      summary: Get all cases
      security:
        - bearerAuth: []
      responses:
        '200':
          description: List of cases
          content:
            application/json:
              schema:
                type: array
                items:
                  type: object
                  properties:
                    id:
                      type: string
                    title:
                      type: string
                    status:
                      type: string

  /api/cases/{id}:
    put:
      summary: Update a case
      security:
        - bearerAuth: []
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                status:
                  type: string
              required:
                - status
      responses:
        '200':
          description: Case updated
          content:
            application/json:
              schema:
                type: object
                properties:
                  id:
                    type: string
                  status:
                    type: string

    delete:
      summary: Delete a case
      security:
        - bearerAuth: []
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Case deleted
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string

  /api/notifications:
    post:
      summary: Send a notification
      security:
        - bearerAuth: []
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                caseId:
                  type: string
                message:
                  type: string
              required:
                - caseId
                - message
      responses:
        '200':
          description: Notification sent
          content:
            application/json:
              schema:
                type: object
                properties:
                  status:
                    type: string
                  timestamp:
                    type: string
                    format: date-time

components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT
