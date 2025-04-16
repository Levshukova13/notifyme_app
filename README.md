# notifyme_app

This is a fictional REST API documentation created for a sample notification app (NotifyMe). It demonstrates how I structure endpoints, explain request/response formats, and present developer-friendly technical content.

---

## 📘 Overview
The NotifyMe API allows users to subscribe to employee-related events, manage their preferences, and receive notifications. 

**Base URL:** `https://api.notifyme.io/v1`

---

## 🔐 Authentication
All requests require an API token sent in the Authorization header:
```http
Authorization: Bearer YOUR_API_TOKEN
```

---

## 🔗 Endpoints

| Method | Endpoint                | Description                          |
|--------|--------------------------|--------------------------------------|
| GET    | `/events`               | Retrieve a list of available events  |
| POST   | `/subscriptions`        | Subscribe to specific events         |
| GET    | `/subscriptions`        | View all user subscriptions          |
| DELETE | `/subscriptions/{id}`   | Cancel a specific subscription       |
| POST   | `/users/register`       | Register a new user                  |

---

## 📥 Sample Requests & Responses

### 🔹 GET /events
Retrieve all available event types.

**Request:**
```http
GET /events HTTP/1.1
Authorization: Bearer test_token
```

**Response:**
```json
[
  { "id": "1", "name": "New Hire" },
  { "id": "2", "name": "Birthday" },
  { "id": "3", "name": "Promotion" },
  { "id": "4", "name": "Work Anniversary" }
]
```

---

### 🔹 POST /subscriptions
Subscribe to specific event types.

**Request:**
```json
{
  "userId": "12345",
  "eventIds": ["1", "3"]
}
```

**Response:**
```json
{
  "message": "Subscribed successfully.",
  "subscriptions": [
    { "eventId": "1", "eventName": "New Hire" },
    { "eventId": "3", "eventName": "Promotion" }
  ]
}
```

---

### 🔹 DELETE /subscriptions/{id}
Cancel a subscription.

**Request:**
```http
DELETE /subscriptions/3 HTTP/1.1
Authorization: Bearer test_token
```

**Response:**
```json
{
  "message": "Subscription deleted successfully."
}
```

---

### 🔹 POST /users/register
Register a new user in the system.

**Request:**
```json
{
  "name": "Anna Kowalska",
  "email": "anna.kowalska@example.com"
}
```

**Response:**
```json
{
  "userId": "12345",
  "message": "User registered successfully."
}
```

---

### 🔹 POST /notifications/test
Send a test notification to the current user (for development purposes).

**Request:**
```json
{
  "userId": "12345",
  "event": "New Hire",
  "message": "A new team member has joined!"
}
```

**Response:**
```json
{
  "status": "sent",
  "timestamp": "2025-04-16T10:30:00Z"
}
