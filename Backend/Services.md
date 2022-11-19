# Architecture
The architecture is a SOA-based architecture. For simplicity resonse we are only using one database for all services.

![Image of Architecture](images/backend-architecture.drawio.png)

# Services

| Name  | Responsiblity  | Repository URL  |
|---|---|---|
|  User Management | Login users, Register Users, Create JWT Token, Validate JWT Token, Creating organization chart, defining roles, Ebenen und Gruppen verwalten, Firmen/Kunden verwalten | https://github.com/Projekt-DataScience/backend-user_management  |
| Audit  |  Audit functionality (Manage Audits, Questions, Answers etc.) | https://github.com/Projekt-DataScience/backend-audit  |
| Tasks  |  Gathers tasks from all apps for a specific user, so frontend can display it in Frontend under "Aktuelle Aufgaben" (see Dashboard/page 2 of Mockup) | https://github.com/Projekt-DataScience/backend-tasks  |

# Datenbankschema

Siehe [backend-db-lib README](https://github.com/Projekt-DataScience/backend-db-lib/blob/main/README.md)
