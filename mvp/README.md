# Proctique Arquitecture
Proctique is a Project Discovery Platform where authors can showcase their work, and users can explore, evaluate, and leave meaningful reviews on published projects. The platform also includes an administrative layer that moderates the community and manages authors, projects, categories, and reviews to ensure a healthy and organized ecosystem.

## Project elements

Clients 
1. Users
2. Authors
3. Admin

Frontends (Views)
1. Reviews
2. Projects
3. Admin Dashboard
4. Auth

Backend
1. Reviews
2. Projects
3. Auth
4. Email Event Queue (Queue)
5. Send New review email (Notification)
6. Send Reset password email (Notification)
7. Send Project published email (Notification)

Storages
1. Main database
2. Image storage (File storage)

## Project Patterns

1. Client–Server
2. Modular monolith
3. Event-Driven (queue)
4. Role-based access control

## Communication

1. Frontend - Backend [RestAPI] [Synchronous]
2. Backend - Queue [Queues/Events] [Asynchronous]
3. Backend - Database [Storage] [Synchronous]
4. Backend - Image Storage [Storage] [Synchronous]

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

![Proctique MVP diagram](mvp-diagram.png)

*Legend*
![Proctique MVP diagram legend](legend.png)

*Note: For MVP we are not going to use any external service* 

*Note: You can review on Figjam [here](https://www.figma.com/board/FaCHliTP4UXuOrhvpX1UHV/M4-HS-Designing-APIs?node-id=32-361)*