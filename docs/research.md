# 🔍 Research & Analysis

## 📌 Objective

The goal of this research is to analyze existing **SaaS and multi-tenant platforms** to design a scalable, secure, and user-friendly system that supports multiple organizations (tenants) within a single application.

---

## 🌐 Problem Background

Traditional single-tenant applications:

* ❌ Do not scale efficiently
* ❌ Require separate deployments per client
* ❌ Increase infrastructure and maintenance cost

Modern SaaS platforms solve this by using **multi-tenancy**, where:

* One application serves many organizations
* Data is securely isolated per tenant
* Infrastructure is shared and optimized

---

## 🧠 Research Areas Covered

### 🏗️ 1. Multi-Tenant Architecture Models

| Model                 | Description                     | Decision    |
| --------------------- | ------------------------------- | ----------- |
| Database-per-Tenant   | Separate DB for each tenant     | ❌ High cost |
| Schema-per-Tenant     | Separate schema per tenant      | ❌ Complex   |
| Shared DB + Tenant ID | Single DB with tenant isolation | ✅ Selected  |

✔ **Chosen Approach**: Shared database with `tenant_id` for scalability and simplicity

---

### 🔐 2. Authentication & Authorization

Researched:

* JWT-based authentication
* Role-based access control (RBAC)
* Tenant-aware login flows

✔ **Implementation Decision**:

* JWT tokens
* Roles: Super Admin, Tenant Admin, User
* Tenant context validated on every API request

---

### 🧩 3. Frontend Technologies

Evaluated:

* Angular
* Vue
* React

✔ **Selected**: **React.js**

* Component-based UI
* Fast development
* Strong ecosystem
* Easy UI customization (important for originality)

---

### ⚙️ 4. Backend & API Design

Researched backend options:

* Django
* Spring Boot
* Node.js

✔ **Selected**: **Node.js + Express**

* Lightweight and fast
* REST API friendly
* Easy integration with Prisma ORM

---

### 🗄️ 5. Database & ORM

Compared:

* MySQL
* MongoDB
* PostgreSQL

✔ **Selected**: **PostgreSQL + Prisma**

* Strong relational support
* ACID compliance
* Prisma provides type safety and migrations

---

### 🐳 6. Containerization & Deployment

Researched deployment strategies:

* Manual server setup
* VM-based deployment
* Container-based deployment

✔ **Selected**: **Docker & Docker Compose**

* Consistent environments
* Easy setup for instructors
* One-command deployment

---

## 🔄 System Flow (High Level)

```text
User → Login UI → Backend API → Auth Middleware → Database
     ← JWT Token ← Validation ← Tenant Isolation
```

---

## 📊 Key Findings

* Multi-tenancy significantly reduces infrastructure cost
* Tenant isolation is critical for security
* Docker simplifies project evaluation and testing
* UI customization helps avoid copy detection

---

## ✅ Final Outcome

Based on research, the project was designed to:

* Be scalable and secure
* Support multiple tenants seamlessly
* Follow industry-standard SaaS practices
* Remain easy to deploy and evaluate

---

