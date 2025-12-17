
# Representative API Endpoints

## 1. User Authentication – Login

Endpoint

```
POST /api/auth/login
```

Description

Authenticates a user and returns a JWT used for authorized requests.

Request

```
{
  "email": "user@example.com",
  "password": "securePassword123"
}
```

Response – 200 OK

```
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "u_123",
    "role": "USER",
    "name": "Jane Doe"
  }
}
```

## 2. Get Published Projects (Public)

Endpoint

```
GET /api/projects
```

Description

Returns a paginated list of published projects visible to all users.

Request

```
GET /api/projects?page=1&limit=10
```

Response – 200 OK

```
{
  "items": [
    {
      "id": "p_001",
      "title": "AI Expense Tracker",
      "author": {
        "id": "a_12",
        "name": "Carlos M."
      },
      "coverImageUrl": "/images/p_001.png",
      "publishedAt": "2025-03-12T10:15:00Z"
    }
  ],
  "total": 42
}
```

## 3. Create Review (Authenticated User)

Endpoint

```
POST /api/projects/{projectId}/reviews
```

Description

Allows an authenticated user to leave a review on a published project.

Headers

```
Authorization: Bearer <JWT>
```

Request

```
{
  "rating": 5,
  "comment": "Great project! Very clean architecture."
}
```

Response – 201 Created

```
{
  "id": "r_789",
  "projectId": "p_001",
  "author": {
    "id": "u_123",
    "name": "Jane Doe"
  },
  "rating": 5,
  "comment": "Great project! Very clean architecture.",
  "createdAt": "2025-03-15T14:32:00Z"
}
```

## 4. Create Report (Project or Review)

Endpoint

```
POST /api/reports
```

Description

Allows a user to report a project or review for moderation.

Headers

```
Authorization: Bearer <JWT>
```

Request

```
{
  "targetType": "PROJECT",
  "targetId": "p_001",
  "reason": "Inappropriate content",
  "description": "This project contains offensive language."
}
```

Response – 201 Created

```
{
  "id": "rep_456",
  "status": "PENDING",
  "targetType": "PROJECT",
  "targetId": "p_001",
  "createdAt": "2025-03-16T09:10:00Z"
}
```

## 5. Approve Report (Admin Only)

Endpoint

```
POST /api/reports/{reportId}/approve
```

Description

Allows an admin to approve a report and trigger moderation actions.

Headers

```
Authorization: Bearer <JWT>
```

Request

```
{
  "moderationNote": "Confirmed violation of community guidelines."
}
```

Response – 200 OK

```
{
  "id": "rep_456",
  "status": "APPROVED",
  "actionTaken": "PROJECT_UNPUBLISHED",
  "resolvedAt": "2025-03-16T09:20:00Z"
}
```