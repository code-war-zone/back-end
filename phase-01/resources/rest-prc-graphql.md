# REST vs RPC vs GraphQL

Modern backend systems communicate using different **API architectural styles**.

The three most common are:

- REST (Representational State Transfer)
- RPC (Remote Procedure Call)
- GraphQL

Each style has different:

- design philosophy
- performance characteristics
- scalability patterns
- frontend implications

---

## 1. High-Level Comparison

| Feature       | REST           | RPC                 | GraphQL        |
| ------------- | -------------- | ------------------- | -------------- |
| Core idea     | Resources      | Functions / Actions | Data Queries   |
| Endpoints     | Many           | Few                 | Single         |
| Data control  | Server decides | Server decides      | Client decides |
| Overfetching  | Yes            | Yes                 | No             |
| Underfetching | Yes            | Yes                 | No             |
| Versioning    | Common         | Common              | Rare           |
| Caching       | Excellent      | Difficult           | Difficult      |
| Flexibility   | Medium         | Low                 | Very high      |
| Complexity    | Low            | Medium              | Medium–High    |

---

## 2. REST

## 2.1 Concept

REST is **resource-oriented**.

Everything is treated as a **resource identified by a URL**.

Examples:

/users
/products
/orders/10

Operations are performed using **HTTP methods**:

| Method | Meaning  |
| ------ | -------- |
| GET    | retrieve |
| POST   | create   |
| PUT    | update   |
| DELETE | delete   |

---

## 2.2 Example

### Request

GET /users/10

### Response

```json
{
  "id": 10,
  "name": "Sam",
  "email": "sam@email.com"
}


⸻

2.3 Characteristics
	•	Stateless
	•	Cache-friendly
	•	Clear URL structure
	•	Uses HTTP semantics correctly
	•	Easy to learn
	•	Widely adopted

⸻

2.4 Limitations
	•	Overfetching
	•	Underfetching
	•	Many endpoints to maintain
	•	Versioning complexity

Example:

/api/v1/users
/api/v2/users


⸻

2.5 Best Use Cases
	•	Public APIs
	•	CRUD applications
	•	Standard web services
	•	Microservices with simple data flows

⸻

3. RPC

3.1 Concept

RPC is action-oriented.

Client calls a remote function on the server.

It feels like calling a local method.

Common technologies:
	•	JSON-RPC
	•	XML-RPC
	•	gRPC

⸻

3.2 Example

Endpoint

POST /createUser

Request Body

{
  "name": "Sam",
  "email": "sam@email.com"
}

Another example:

POST /calculateDiscount


⸻

3.3 Characteristics
	•	Function-driven design
	•	Fewer endpoints
	•	Strong typing (gRPC)
	•	High performance
	•	Efficient serialization (Protocol Buffers)

⸻

3.4 Limitations
	•	Tight client-server coupling
	•	Harder HTTP caching
	•	Not resource-intuitive
	•	Harder API discoverability

⸻

3.5 Best Use Cases
	•	Internal microservices communication
	•	High-performance systems
	•	Real-time services
	•	Streaming platforms
	•	Service mesh architectures

⸻

4. GraphQL

4.1 Concept

GraphQL is a query language for APIs.

Client specifies exactly what data it needs.

Usually exposed via a single endpoint:

POST /graphql


⸻

4.2 Example Query

query {
  user(id: 10) {
    name
    email
  }
}

Response

{
  "data": {
    "user": {
      "name": "Sam",
      "email": "sam@email.com"
    }
  }
}


⸻

4.3 Characteristics
	•	No overfetching
	•	No underfetching
	•	Strong schema definition
	•	Nested data retrieval in one request
	•	Client-driven data shape

⸻

4.4 Limitations
	•	Higher backend complexity
	•	Query cost management required
	•	Hard caching strategies
	•	Security risks with deep queries

⸻

4.5 Best Use Cases
	•	Large frontend applications
	•	Mobile apps with bandwidth constraints
	•	API aggregation gateways
	•	Complex dashboards and analytics apps

⸻

5. Endpoint Design Comparison

REST

GET /users
GET /users/10
GET /users/10/orders

RPC

POST /getUser
POST /getUserOrders
POST /createOrder

GraphQL

POST /graphql

Query determines returned data.

⸻

6. Data Fetching Behavior

REST Overfetching Example

GET /users/10

Returns:
	•	id
	•	name
	•	email
	•	address
	•	phone
	•	createdAt

Even if frontend only needs:

name

GraphQL Solution

Client query:

user(id: 10) {
  name
}

Server returns only requested fields.

⸻

7. Performance Comparison


| Aspect              | REST   | RPC    | GraphQL  |
|---------------------|--------|--------|--------- |
| Network round trips | Medium | Low    | Very low |
| Payload size        | Medium | Small  | Optimal  |
| Server complexity   | Low    | Medium | High     |
| Caching efficiency  | High   | Low    | Low      |
⸻

8. Versioning Strategy

REST

URL versioning:

/api/v1/users
/api/v2/users

RPC

Function versioning:

createUserV2()

GraphQL
	•	Schema evolves gradually
	•	Versioning usually avoided

⸻

9. Real-World Adoption
	•	REST → most public APIs
	•	gRPC → Google, Netflix, internal infrastructures
	•	GraphQL → Meta, GitHub, Shopify

⸻

10. Final Summary
	•	REST → simple, stable, resource-based
	•	RPC → fast, function-based, backend-friendly
	•	GraphQL → flexible, frontend-optimized


```
