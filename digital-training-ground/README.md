# Digital Training Ground

> System analysis and architecture case study for an internal platform that manages student projects and provides infrastructure resources for project teams.

## Project overview

Digital Training Ground is an internal platform designed to centralize the management of educational projects, student teams and infrastructure resources.

The system provides a single workflow for project creation, team management and automated provisioning of the resources required for project work.

## My role

**System Analyst/Project Lead**

I was responsible for requirements analysis, system design and coordination of a 9-person project team.

## Key results

- Formalized functional and non-functional requirements and defined the system boundaries, roles and key user scenarios.
- Designed the target architecture of the platform and interactions between application, infrastructure and external services.
- Designed automated provisioning of project environments: VM creation in Proxmox, repository creation in Gitea and file storage provisioning in Nextcloud.
- Defined integration and failure scenarios, including service unavailability, operation retries, status control and access management.
- Coordinated a 9-person team and aligned analytical, architectural and implementation decisions.

## Architecture

The solution is based on a web application with a **FastAPI backend** and **PostgreSQL** database.

The platform integrates with:

- **LDAP** — authentication and role-based access
- **Proxmox VE** — virtual machine provisioning
- **Gitea** — project repositories
- **Nextcloud** — project file storage
- **OpenVPN** — secure remote access to the internal environment

The backend contains dedicated modules for authentication, project and team management, infrastructure provisioning, resource scheduling and external integrations.

## Key scenarios

The system covers the complete project setup workflow:

**Project creation - Team formation - Resource provisioning - Access assignment - Project work**

After a team is formed, the platform automatically provisions the required infrastructure and assigns access rights to team members.

## Artifacts

Detailed project artifacts are available in this repository:

- Requirements specification
- System architecture
- UML and interaction diagrams
- Data model
- Integration and failure scenarios

## Technology&Methods

`System Analysis` `UML` `REST API` `PostgreSQL` `FastAPI` `LDAP` `Proxmox VE` `Gitea` `Nextcloud` `OpenVPN` `Git` `Linux`
