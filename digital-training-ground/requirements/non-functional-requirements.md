# Non-Functional Requirements

This document defines the key non-functional requirements and architectural constraints for the Digital Training Ground platform.

## NFR-01. Security

The platform shall operate within the faculty's internal network.

Remote access to the platform shall be available only through the faculty VPN.

User authentication shall be performed through the existing LDAP directory.

Access to system functionality and project resources shall be restricted according to user roles and project membership.

## NFR-02. Access Control

The system shall implement role-based access control (RBAC).

Permissions shall be determined by the authenticated user's role and participation in a specific project or team.

Users shall not have access to infrastructure resources assigned to other project teams unless explicitly authorized.

## NFR-03. Reliability

Failure of an integrated infrastructure service shall not result in loss of the project or team data stored by the platform.

The system shall preserve the state of infrastructure provisioning operations and allow failed operations to be retried.

Repeated requests shall not result in unintended duplicate infrastructure resources.

## NFR-04. Data Consistency

The system shall maintain consistency between project data and the state of provisioned infrastructure resources.

Provisioning operations shall have explicit execution states that allow the system to determine whether an operation is pending, completed or failed.

## NFR-05. Performance

User-facing operations that do not require infrastructure provisioning shall be processed without unnecessary dependency on external infrastructure services.

Long-running infrastructure operations shall not block interaction with the main application.

The current state of such operations shall be available to the user.

## NFR-06. Maintainability

The backend shall separate responsibilities between authentication, project management, team management, infrastructure provisioning and external service integration.

Integration logic for external systems shall be isolated from the core business logic to reduce coupling between components.

## NFR-07. Observability

The system shall log significant application and infrastructure operations.

Logs shall provide sufficient information to identify failed provisioning and integration operations and support troubleshooting.

## NFR-08. Network Constraints

The application shall not require public Internet exposure.

Access from the faculty network shall be available directly within the internal network.

Remote users shall establish a VPN connection before accessing the application.

External infrastructure services used by the platform shall be accessible from the application environment within the internal network.
