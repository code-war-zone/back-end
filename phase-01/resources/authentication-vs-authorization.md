# Authentication vs Authorization

Authentication and Authorization are two core concepts in **application security** and **API design**.

They are often confused but serve **different purposes**.

- **Authentication → Who are you?**
- **Authorization → What are you allowed to do?**

## 1. Authentication

### 1.1 Definition

Authentication is the process of **verifying the identity of a user or system**.

It answers the question:

> Is this user really who they claim to be?

### 1.2 Common Authentication Methods

### Password-based Authentication

User provides:

- username
- password

Example:

POST /login

```json
{
  "email": "sam@email.com",
  "password": "secret"
}
```

Token-based Authentication (JWT)

After successful login:
• server generates a token
• client sends token with each request

Example header:

````txt
Authorization: Bearer <token>

```id="0hx3qt"
````

### Session-based Authentication

- server stores session in memory or database
- client stores session ID in cookie

### Multi-Factor Authentication (MFA)

User must provide:

- password
- OTP code
- biometric verification

## 1.3 Authentication Characteristics

- Happens **before authorization**
- Confirms identity
- Usually occurs at login
- Can involve encryption and hashing

## 2. Authorization

### 2.1 Definition

Authorization is the process of **determining what an authenticated user is allowed to access or perform**.

It answers the question:

> Does this user have permission?

### 2.2 Example

User is authenticated:

- user ID = 10
- role = "customer"

Authorization rules:

- can view own orders
- cannot access admin dashboard

Example:

GET /admin/dashboard

Server response:

403 Forbidden

---

### 2.3 Authorization Models

### Role-Based Access Control (RBAC)

Permissions are based on **user roles**.

Example roles:

- admin
- manager
- customer

### Attribute-Based Access Control (ABAC)

Permissions depend on:

- user attributes
- resource attributes
- environment conditions

Example:

- user can edit document only during working hours

### Policy-Based Authorization

Uses centralized policy engines.

Common in:

- cloud systems
- microservices
- service meshes

## 3. Authentication vs Authorization (Comparison)

| Aspect         | Authentication   | Authorization      |
| -------------- | ---------------- | ------------------ |
| Purpose        | Verify identity  | Verify permissions |
| Question       | Who are you?     | What can you do?   |
| Happens first  | Yes              | No                 |
| Requires login | Yes              | Not always         |
| Failure code   | 401 Unauthorized | 403 Forbidden      |

## 4. Typical Request Flow

Client → Login → Server authenticates user
Client → Sends token → Server authorizes action

Flow example:

1. User logs in → receives token
2. User requests protected resource
3. Server validates token (authentication)
4. Server checks permissions (authorization)
5. Server returns response

## 5. Real-World Example

Banking system:

Authentication:

- user enters password + OTP

Authorization:

- user allowed to view balance
- user not allowed to view other accounts

## 6. Best Practices

- Always separate authentication and authorization logic
- Use secure token storage
- Implement least-privilege access
- Use HTTPS for all authentication flows
- Expire tokens and sessions properly

## 7. Summary

- **Authentication identifies the user**
- **Authorization controls user access**

Both are essential for building **secure APIs and applications**.
