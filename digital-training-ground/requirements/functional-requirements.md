# Functional Requirements

This document defines the core functional requirements for the Digital Training Ground platform.

## FR-01. User authentication

The system shall authenticate users through the faculty LDAP directory.

After successful authentication, the system shall determine the user's role and provide access to functionality according to the assigned permissions.

Supported roles:
- Administrator
- Lead Teacher
- Teacher
- Student

## FR-02. Project management

The system shall allow authorized teachers to:
- create and edit educational projects;
- define project descriptions and deadlines;
- define project milestones;
- view project status and participating teams.

## FR-03. Team management

The system shall support student team formation.

Teachers shall be able to:
- create teams manually;
- assign students to teams;
- form teams based on academic groups;
- assign team roles.

Each student shall have access only to the projects and resources assigned to their team.

## FR-04. Project environment provisioning

After a project team is formed, the system shall provide the infrastructure resources required for project work.

The provisioning workflow shall include:
- creation of a virtual machine in Proxmox VE;
- creation of a Git repository in Gitea;
- creation of project file storage in Nextcloud;
- assignment of access permissions to team members.

The system shall store the provisioning status of each resource.

## FR-05. Infrastructure management

The system shall allow authorized users to:
- request project environments;
- view allocated infrastructure resources;
- monitor provisioning status;
- manage the lifecycle of project environments.

## FR-06. External service integration

The system shall integrate with:
- LDAP for authentication and role resolution;
- Proxmox VE for virtual machine provisioning;
- Gitea for repository creation;
- Nextcloud for project file storage.

Integration operations shall be performed through the corresponding service interfaces/APIs.

## FR-07. Failure handling

The system shall track the execution status of infrastructure provisioning operations.

If an external service is unavailable or an operation fails, the system shall:
- record the failure;
- preserve the current provisioning state;
- prevent duplicate resource creation;
- allow the operation to be retried.

## FR-08. Access control

The system shall enforce role-based access control.

Access to projects, teams and infrastructure resources shall be granted according to the user's role and project membership.

## FR-09. Project status tracking

The system shall provide information about:
- project status;
- team composition;
- allocated resources;
- infrastructure provisioning status;
- project milestones and deadlines.
