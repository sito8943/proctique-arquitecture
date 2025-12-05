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

1. Frontend - Backend via Rest API
2. Backend - Queue via events

## AuthN and AuthZ

JWT for authentication and Role-Based for Authorization

## MVP Diagram

![Proctique MVP diagram](mvp-diagram.png)

*Legend*
![Proctique MVP diagram legend](legend.png)

*Note: You can review on Figjam [here](https://www.figma.com/board/FaCHliTP4UXuOrhvpX1UHV/M4-HS-Designing-APIs?node-id=32-361)*