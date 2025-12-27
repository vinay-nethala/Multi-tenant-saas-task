# Multi-Tenant SaaS Platform API Reference

## Authentication & Security Overview

- **Auth method:** JWT Bearer token
- **Header format:**

Authorization: Bearer <token>



- **Token valid for:** 24 hours
- **Base URL for API (local):**

http://localhost:5000/api


---

## 1. System Health Endpoint

Verify the backend service and database connection are active.

- **HTTP Method:** GET  
- **URL:** `/health`  
- **Access:** Public (no authentication needed)  

**Success Response (200 OK):**

```json
{
"status": "ok",
"database": "connected"
}
```
### 2. User Authentication Endpoints
### 2.1 Tenant Registration
Register a new tenant (organization) with its first admin user.

Method: POST

Route: /auth/register-tenant

Access: Public

Request Body:

```json

{
  "tenantName": "Acme Corp",
  "subdomain": "acme",
  "adminEmail": "admin@acme.com",
  "password": "SecurePassword123"
}
```
Response (201 Created):

```bash
{
  "message": "Tenant registered successfully",
  "tenantId": "uuid-string"
}
```
### 2.2 User Login
### Authenticate existing users and receive a JWT token.

Method: POST

Route: /auth/login

Access: Public

Request Body:

json
{
  "email": "admin@acme.com",
  "password": "SecurePassword123"
}
Response (200 OK):

json
{
  "token": "<jwt-token>",
  "user": {
    "id": "uuid",
    "email": "admin@acme.com",
    "role": "tenant_admin",
    "tenantId": "uuid"
  }
}
### 2.3 Get Logged-in User Info
### Fetch details of the currently authenticated user.

Method: GET

Route: /auth/me

Access: Requires valid JWT token (all roles)

Response (200 OK):

json

{
  "user": {
    "id": "uuid",
    "fullName": "John Doe",
    "email": "john@acme.com",
    "role": "user"
  }
}
### 3. Tenant Administration (Super Admin Access Only)
###3.1 Retrieve All Tenants
Get a list of all tenants registered in the system.

Method: GET

Route: /tenants

Access: Super Admin only

Response:

json
{
  "status": "success",
  "results": 2,
  "data": {
    "tenants": [
      { "id": "1", "name": "Acme Corp", "subdomain": "acme" },
      { "id": "2", "name": "Beta Inc", "subdomain": "beta" }
    ]
  }
}
### 3.2 Get Details of a Tenant
### Retrieve detailed info for a tenant by ID.

Method: GET

Route: /tenants/:id

Access: Super Admin only

Response:

json

{
  "id": "uuid",
  "name": "Acme Corp",
  "status": "active"
}
### 3.3 Modify Tenant Data
### Update tenant information such as name or status.

Method: PUT

Route: /tenants/:id

Access: Super Admin only

Request Body:

json

{
  "name": "Acme Global",
  "status": "inactive"
}
## 4. User Operations (Tenant Admin)
## 4.1 Get Tenant Users List
## Fetch all users that belong to a tenant.

Method: GET

Route: /tenants/:tenantId/users

Access: Tenant Admin only

Response:

json

{
  "data": {
    "users": [
      { "id": "u1", "fullName": "Alice", "role": "user" }
    ]
  }
}
## 4.2 Add a New User
## Create a new user under a tenant.

Method: POST

Route: /tenants/:tenantId/users

Access: Tenant Admin only

Request Body:

json

{
  "email": "alice@acme.com",
  "password": "Password123",
  "fullName": "Alice Smith",
  "role": "user"
}
## 4.3 Edit User Details
## Update user profile info or role.

Method: PUT

Route: /users/:id

Access: Tenant Admin only

Request Body:

json

{
  "fullName": "Alice Jones",
  "role": "tenant_admin"
}
## 4.4 Delete a User
## Remove a user from the tenant.

Method: DELETE

Route: /users/:id

Access: Tenant Admin only

## 5. Project Management APIs
## 5.1 List Projects of Tenant
List all projects under the requesting tenant.

Method: GET

Route: /projects

Access: All logged-in users (User, Admin)

Response:

json
{
  "data": {
    "projects": [
      { "id": "p1", "title": "Website Redesign", "status": "active" }
    ]
  }
}
## 5.2 Create New Project
## Add a project inside a tenant’s scope.

Method: POST

Route: /projects

Access: Tenant Admin only

Request Body:

json
{
  "title": "Q3 Marketing Campaign",
  "description": "Planning for Q3",
  "status": "active"
}
## 5.3 Get Project Information
## Fetch detailed data about a specific project.

Method: GET

Route: /projects/:id

Access: User or Admin

## 5.4 Update Project Info
## Modify details of a project.

Method: PUT

Route: /projects/:id

Access: Tenant Admin only

Request Body:

json

{
  "status": "completed"
}
Note: Project deletion is commonly done via:

Method: DELETE

Route: /projects/:id

## 6. Task Management
## 6.1 Retrieve Tasks for a Project
Get all tasks under a specific project.

Method: GET

Route: /projects/:projectId/tasks

Access: User / Admin

Response:

json
{
  "data": {
    "tasks": [
      { "id": "t1", "title": "Draft content", "status": "TODO" }
    ]
  }
}
## 6.2 Add a New Task
## Create a task in a project.

Method: POST

Route: /projects/:projectId/tasks

Access: Tenant Admin only

Request Body:

json

{
  "title": "Fix Header Bug",
  "description": "CSS issue on mobile",
  "priority": "HIGH",
  "dueDate": "2023-12-31"
}
## 6.3 Change Task Status
## Update the status of a task quickly (for example, in Kanban views).

Method: PATCH

Route: /tasks/:id/status

Access: User / Admin

Request Body:

json
{
  "status": "IN_PROGRESS"
}
## 6.4 Update Task Details Fully
Modify all task information.

Method: PUT

Route: /tasks/:id

Access: Tenant Admin only

Request Body:

json

{
  "title": "Fix Header Bug (Updated)",
  "priority": "MEDIUM"
}
