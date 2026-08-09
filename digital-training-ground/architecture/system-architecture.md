# System Architecture

This document describes the target architecture of the Digital Training Ground platform and the interaction between its application, infrastructure and external service components.

## Architecture overview

The platform is designed as an internal web-based system operating within the faculty network.

The application layer follows a monolithic architecture with a modular backend. The backend acts as the central orchestration point for project management, team management and infrastructure provisioning.

Remote users access the platform through VPN, while users inside the faculty network can access it directly.

## Core components

### Web UI

Provides the user interface for teachers, administrators and students.

The Web UI communicates with the backend through HTTP/HTTPS API requests.

### Backend

The backend is implemented as a modular application based on FastAPI.

It contains the following logical modules:

- Authentication Module
- Project Management Module
- Team Management Module
- Infrastructure Module
- Resource Scheduler
- Integration Module

The backend contains the main business logic and coordinates interactions with infrastructure and external services.

### PostgreSQL

Stores application data, including:

- users and roles;
- projects;
- project milestones;
- teams and memberships;
- infrastructure resource assignments;
- provisioning states.

## Authentication and access

User authentication is performed through the existing LDAP directory.

After successful authentication, the backend determines the user's role and permissions.

Remote access to the platform is available only through OpenVPN.

Access to project functionality and infrastructure resources is controlled using role-based access control (RBAC).

## Infrastructure provisioning

When a project team requires an isolated working environment, the backend coordinates resource provisioning.

The Infrastructure Module requests VM creation through the Proxmox VE REST API.

The Resource Scheduler selects an appropriate Proxmox node based on available infrastructure resources.

The created virtual machine becomes the project environment assigned to the corresponding team.

## External integrations

The platform integrates with existing faculty services.

### Proxmox VE

Used for provisioning and managing virtual machines for project teams.

### Gitea

Used for creating and managing project repositories.

### Nextcloud

Used for provisioning project file storage.

### LDAP

Used as the centralized authentication source and for retrieving user identity information.

### OpenVPN

Provides secure remote access to the internal platform.

## Provisioning workflow

After a project team is formed, the backend can initiate automated provisioning of project resources.

The workflow includes:

1. Validate project and team configuration.
2. Select an infrastructure node.
3. Create a project VM in Proxmox VE.
4. Create a project repository in Gitea.
5. Create project file storage in Nextcloud.
6. Assign access permissions to team members.
7. Store resource identifiers and provisioning status in PostgreSQL.

Provisioning operations are tracked by the backend to prevent inconsistent resource states and support controlled retries in case of integration failures.

## Architectural decisions

The architecture follows several key principles:

- centralized orchestration of project and infrastructure operations;
- reuse of existing faculty infrastructure services;
- isolation of project environments;
- role-based access control;
- modular separation of backend responsibilities;
- controlled handling of integration failures;
- operation inside the faculty's protected network perimeter.
