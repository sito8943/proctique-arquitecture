# Proctique Arquitecture
Proctique is a Project Discovery Platform where authors can showcase their work, and users can explore, evaluate, and leave meaningful reviews on published projects. The platform also includes an administrative layer that moderates the community and manages authors, projects, categories, and reviews to ensure a healthy and organized ecosystem.

## Project elements

### Clients 
1. Users (Normal users)
2. Authors 
3. Admin

### Frontends (Views)
1. Reviews

Allow authenticated users to submit reviews.

2. Projects

Public browsing and discovery of published projects


3. Admin Dashboard

Moderation and Management interface for reports, projects, and reviews.

4. Auth

User authentication.

### Backend
1. Reviews

Handles creation and retrieval of reviews

2. Projects

Manages project lifecycle (create, publish, unpublish).


3. Auth

Handles authentication and JWT issuance.

4. Email Event Queue (Queue)

Receives domain events related to emails.

5. Send New review email (Notification)
6. Send Reset password email (Notification)
7. Send Project published email (Notification)

Send Notification workers send their respective notifications

Storages
1. Main database
2. Image storage (File storage)

For now we have a single main database, which is used for core data, complemented by a dedicated image storage service for media files. This ensures strong consistency for core entities (projects, reviews, users). Separates binary file storage from relational data. Enables efficient image delivery and future CDN integration. And simplifies backup and data management strategies.

## Project Patterns

1. Client–Server

Proctique is designed using a client–server architecture where multiple client applications communicate with backend services through REST APIs.
This decouples user interfaces from business logic, allowing independent evolution and supports future expansion (mobile apps, external integrations) without changing core services.

2. Modular monolith

The backend is implemented as a modular monolith, with clearly separated domains (Auth, Projects, Reviews, Notifications) within a single deployable unit. This reduces operational complexity for MVP and early phases. Encourages clear domain boundaries without the overhead of distributed systems. Makes refactoring into microservices possible in later phases if scaling or team size requires it.

3. Event-Driven (queue)

Asynchronous tasks such as email notifications are handled through an event queue and background workers. This Prevents user-facing actions from being blocked by slow operations (e.g., email sending). Allows independent scaling of background jobs. Provides a foundation for future features such as analytics or audit logging.

4. Role-based access control

Access to backend capabilities is controlled using role-based access control with roles such as User, Author, and Admin. This simplifies authorization logic across services. Ensures sensitive operations (moderation, management) are protected. And scales well as new roles or permissions are added.

## Communication

1. Frontend - Backend [RestAPI] [Synchronous]
2. Backend - Queue [Queues/Events] [Asynchronous]
3. Backend - Database [Storage] [Synchronous]
4. Backend - Image Storage [Storage] [Synchronous]

Frontend applications communicate with backend services using synchronous REST APIs because this is well-understood and widely supported standard Is easy to document, test, and consume. Suitable for CRUD-based operations common in Proctique and keeps frontend logic simple and predictable.

## Public (Access to the public)

1. Frontend (Public views)
2. Auth Services
3. Projects Services (Only see Published Projects)
4. Reviews Services (Only see and post Reviews)
5. Image Storage [Read]

## Internal (Privately or need to be authenticated)

*Authentication required*

- Projects Services [RestAPI] [JWT] (CRUD) (To manage all need to be admin)

- Reviews Services [RestAPI] [JWT] (CRUD) (To manage all need to be admin)

- Image Storage [Storage] [JWT] (Upload / Delete) 

*Managed by services*

- Main Database [Storage]
- Email Event Queue [Queues/Events]
- Send New Review email [Worker]
- Send Password Reset email [Worker]
- Send Project Published email [Worker]

## AuthN and AuthZ

JWT for authentication and Role-Based for Authorization

Roles:

1. Normal User (Can see published projects and post reviews on projects)

2. Author (Can manage their own projects (CRUD))

3. Admin (Can manage all)

Users (All of them) need to go to the Login View to be able to Sign In or Sign Up, after it:

- Post Reviews
- Manage Projects
- Manage All (For admin only)

But without signing in, all users can see projects in the public project page

## MVP Diagram

![Proctique MVP diagram](diagram.png)

*Legend*
![Proctique MVP diagram legend](legend.png)

*Note: For MVP we are not going to use any external service* 

*Note: You can review on Figjam [here](https://www.figma.com/board/FaCHliTP4UXuOrhvpX1UHV/M4-HS-Designing-APIs?node-id=32-361)*