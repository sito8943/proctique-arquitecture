# Proctique – Project Discovery Platform

Proctique is a Project Discovery Platform where authors can showcase their work, users can explore and review projects, and administrators moderate the community to ensure quality and trust.
The platform evolves incrementally, following a phased architecture approach to balance delivery speed, scalability, and maintainability.

This repository documents the system architecture and capabilities across multiple phases of development.

## Architecture Evolution Overview

Proctique is designed to grow in clearly defined phases, each adding new capabilities while building on the previous one.
- MVP focuses on core discovery, reviews, and basic notifications.
- Phase I introduces moderation and reporting to make the platform production-ready.
- Phase II expands observability, analytics, and scalability to support growth and data-driven decisions.

Each phase is documented independently to clearly show architectural decisions and trade-offs at that stage.

## MVP (Minimum Viable Product)

[Documentation](/mvp/README.md)

### Summary

The MVP establishes the core functionality of Proctique

#### Core functionality
- Authors can publish projects
- Users can browse projects and leave reviews
- Admins can manage content
- Email notifications are sent for key events (new review, project published, password reset)

#### Key Characteristics
- Modular monolith backend
- REST-based client–server communication
- Role-based access control (RBAC)
- Event-driven notifications via a queue
- Public and authenticated API separation

The MVP validates the core product idea with minimal infrastructure complexity.

## Phase I – Production Readiness & Moderation

[Documentation](/phase1/CHANGELOG.md)

### Summary

Phase I focuses on making Proctique ready for public release by adding moderation and governance capabilities.

#### Key Additions
- Reports Service for projects and reviews
- Admin moderation dashboard
- Synchronous orchestration when reports are approved
- Automatic actions:
- Unpublish reported projects
- Hide or delete reported reviews
- New notification flows for report lifecycle events

#### Why Phase I Matters?
- Introduces trust and safety mechanisms
- Enables real admin workflows
- Ensures immediate consistency between moderation decisions and content visibility

## Phase II – Analytics, Scale & Insights

[Documentation](/phase2/CHANGELOG.md)

#### Summary

Phase II focuses on observability, analytics, and scalability, enabling data-driven decisions and platform growth.

#### Key Additions
- Reporting & analytics capabilities
- Moderation and content insights
- Structured datasets for future dashboards
- Preparation for asynchronous, event-driven workflows
- Improved separation of concerns between services

#### Goals of Phase II
- Understand user behavior and content quality
- Support operational insights for admins
- Prepare the platform for higher traffic and feature expansion