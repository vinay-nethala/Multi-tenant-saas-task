## 🚀Multi-Tenant SaaS Platform

A full-stack Multi-Tenant SaaS Platform that allows multiple organizations (tenants) to securely share the same application while keeping their data isolated. The system supports role-based access, project management, and centralized administration using modern web technologies.


 ## 📌 Project Overview

This project demonstrates how real-world SaaS applications work using multi-tenancy architecture, role-based authentication, and containerized deployment.
It is designed for learning, demonstration, and academic evaluation.

---

✨ Key Features

🏢 Multi-tenant architecture (organization-wise data isolation)

👤 Role-based access (Super Admin, Admin, User)

🔐 Secure authentication using JWT

📊 Dashboard with tenant & project insights

🗂️ Project management per tenant

🐳 Fully Dockerized (Frontend + Backend + Database)

---
🛠️ Tech Stack
## Frontend

React.js

React Router

Context API

CSS (Custom styling)

---

## Backend

Node.js

Express.js

Prisma ORM

PostgreSQL
---

DevOps & Tools

Docker & Docker Compose

JWT Authentication

bcrypt (password hashing)

---
```bash

🧱 System Architecture (High Level)
Client (React)
     ↓
API Gateway (Express)
     ↓
Business Logic
     ↓
Database (PostgreSQL)
```


Each tenant’s data is logically separated using tenant IDs.

👥 User Roles
Role	Description
```bash
Super Admin 	"Manages all tenants & system"
Admin        "Manages projects within a tenant"
User	        "Works on assigned projects"
```
---
🔑 Default Login Credentials
```
Super Admin

Email: superadmin@system.com

Password: Admin@123

Demo User

Email: user1@demo.com

Password: User@123
```
---

▶️ How to Run the Project
Prerequisites
```

Docker

Docker Compose

Steps
docker-compose down
docker-compose up --build
```
---


Access the application:
```

Frontend: http://localhost:3000

Backend API: http://localhost:5000
```
---

🧪 How to Test the Project

Login using Super Admin credentials

View tenants and system overview

Login as tenant user

Create and view projects

Verify role-based access control
---

📂 Folder Structure (Simplified)
```bash
Multi-Tenant-SaaS-Platform/
│
├── frontend/
│   └── src/
│
├── backend/
│   ├── prisma/
│   ├── routes/
│   ├── controllers/
│   └── seeds/
│
├── docker-compose.yml
└── README.md
```
---
🎯 Learning Outcomes

Understanding multi-tenant SaaS architecture

Implementing secure authentication & authorization

Using Docker for full-stack deployment

Working with Prisma ORM and PostgreSQL

Building scalable full-stack applications
---

📌 Future Enhancements

Task management module

Subscription billing

Email notifications

Activity audit logs

CI/CD pipeline integration














