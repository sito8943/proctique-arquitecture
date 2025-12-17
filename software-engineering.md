# Proctique – Software engineering

## What does the system do?

Proctique is a Project Discovery and Review Platform that allows creators to publish projects and receive feedback from the community. Users can explore projects, evaluate them, and leave meaningful reviews, while administrators moderate content to ensure quality and community standards. The platform supports project publishing, reviewing, moderation, notifications, and role-based access control.

## Who are the users?

Proctique has three primary user groups:
1. Users: Can browse published projects, discover new work, and leave reviews. (Post-MVP: Ability to report projects and reviews).

2. Authors: Inherit all User permissions with the added ability to create, manage, and publish their own projects. They can also interact with feedback received.

3. Administrators: Responsible for platform moderation, including managing users, projects, and categories, as well as resolving reports to ensure a healthy ecosystem.

## What problems does it solve?

Proctique addresses several common problems in project-sharing communities:
- Lack of a centralized place to discover and evaluate projects beyond simple social media posts.
- Limited opportunities for creators to receive structured, meaningful feedback.
- Difficulty moderating community content at scale without clear workflows.
- Poor visibility and recognition for early-stage or independent projects.

By combining project discovery, reviews, moderation, and role-based permissions, Proctique creates a structured and trustworthy environment for showcasing and evaluating creative and technical work.

## Functional Requirements

- Allow users to register, authenticate, and manage their accounts.
- Allow authors to create, edit, publish, and unpublish projects.
- Allow users to browse and discover published projects.
- Allow users to submit reviews on published projects.
- Allow authors to view and respond to feedback on their projects.
- Allow administrators to manage users, projects, categories, and reviews.
- Allow users to report projects or reviews that violate community guidelines.
- Allow administrators to review, approve, or reject reports.
- Automatically hide or remove content when a report is approved.
- Send email notifications for key events (e.g., new review, report approved, project unpublished).
- Enforce role-based access control (RBAC) across all actions.
- Provide public access to published projects without authentication.
- Provide secure APIs for frontend consumption.

## Non-Functional Requirements

- Background jobs (emails, moderation actions) must not block user interactions.
- Authentication must be handled securely using JWT-based authentication.
- Users may only modify resources they own or are authorized to manage.
- Admin-only actions must be protected at both API and service levels.
- Important domain events (reviews created, reports approved, content hidden) should be auditable.
- Metrics should allow tracking usage patterns and moderation activity over time.
- Users should only be able to edit or delete content they own.
- Users should experience clear feedback when an action succeeds or fails (e.g., submitting a review, reporting content).