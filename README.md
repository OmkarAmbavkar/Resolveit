# 🛠️ ResolveIt – Case Management System

ResolveIt is a secure and scalable case management system built with Node.js and MongoDB. It provides RESTful APIs for user authentication, case registration, case tracking, and notifications.

---

## 🚀 Features

- 🔐 JWT-based user authentication
- 📝 Register and manage cases
- 📂 View and update case status
- 🔔 Send notifications related to cases
- 📚 Swagger-based API documentation

---

## 🧰 Tech Stack

| Layer        | Technology         |
|--------------|--------------------|
| Backend      | Node.js + Express  |
| Database     | MongoDB + Mongoose |
| Auth         | JWT (Bearer Token) |
| API Format   | JSON               |
| Docs         | Swagger (OpenAPI 3.0) |

---

## 📦 Installation

```bash
# Clone the repo
git clone https://github.com/your-username/resolveit.git
cd resolveit

# Install dependencies
npm install

# Create .env file
touch .env

🧩 Key Endpoints
Method	 Endpoint	          Description
POST	  /api/login	        User login
POST	  /api/cases	        Register a new case
GET	    /api/cases	        View all cases
PUT	    /api/cases/:id	    Update case status
DELETE	/api/cases/:id	    Delete a case
POST	  /api/notifications	Send case notification

