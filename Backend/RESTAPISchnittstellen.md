In dieser Datei werden die angebotenen Schnittstellen der Services dokumentiert.

*Für eine genauere Beschreibung der Services siehe [Services.md](./Services.md)*

# User Management
Root-Verzeichnis: `api/user`

## Login

**POST:** `/login`

```json
{
    "email": <email>,
    "password": <password>
}
```

**Antwort (bei erfolgreicher login):**
Response Code: 200

```json
{
   "data": {
    "auth_token": "<jwt_token>"
   }
}
```

**Antwort (bei fehlgeschlagener login):**
Response Code: 401
```json
{
   "data": { 
    "msg": "Authentication failed: Wrong email or password"
   },
}
```

## Logout
**POST:** `/logout`

```json
{
}
```

**Antwort:**
Response Code: 200
```json
{
   "data": {
        "first_name": "firstname",
        "last_name": "lastname"
    }
}
```

## Layer abfragen

**GET:** `/api/layers`
```json
{
   "data": {
        "layers": [
            {
                "id": 1,
                "layer_name": "Mittleres Management",
                "layer_number": 1
            }
        ]
   }
}
```

## Alle Gruppen abrufen
**GET:** `/api/groups`

**Response:**
```json
{
   "data": {
        "groups": [
            {
                "id": 1,
                "group_name": "C-Gruppe",
                "layer": 2
            }
        ]
   }
}
```

## Alle Gruppen unter einem gegebenen Layer abrufen

**GET:** `/api/groups/<layer_id>`

**Response:**
```json
{
   "data": {
        "groups": [
            {
                "id": 1,
                "group_name": "C-Gruppe",
                "layer": <layer_id>
            }
        ]
   }
}
```

# Audit

## Analytics
TODO: muss noch genauer definiert werden

**GET:** `/api/audit/analytics/<audit_id>?month=<monat>&sort_by=<key>&page=<page_number>`

**Response:**
```json
{
   "data": {
        "audit_score": 33,
        "questions":  [
            {
                "title": "Haben alle ausgewiesenen Messmittel eine aktuelle Prüfkette?",
                "question_green": 123,
                "question_yellow": 22,
                "question_red": 445,
                "layer": 1,
                "group": "C-Gruppe"
            }
        ]
    }
}
```

## Offene Audits für eine User

**GET:** `/api/audit/open/`

**Response:**
```json
{
   "data": {
        "audits": [
            {
                "title": "Spontaner Audit in der C-Grupe",
                "layer": 1,
                "due_date": 2022-10-22T00:00:00.000Z,
                "created_by": "Tony Stark"
            },
            {
                "title": "Spontaner Audit in der TN-Grupe",
                "layer": 1,
                "due_date": 2022-10-22T00:00:00.000Z,
                "created_by": "Tony Stark"
            }
        ]
    }
}
```

## Get all Questions

**Get:** `/api/audit/questions`

Response:
```json
{
   "data": {
        "questions": [
            {
                "id": 1,
                "title": "Haben alle ausgewiesenen Messmittel eine aktuelle Prüfkette?",
                "description": "ajsdlfö jasdk lfjasdklf öajds flasdjflk adsjföladsjflak sdfklasd jföl sjdk",
                "category": "Arbeitsschutz",
                "layer": 1,
                "group": "C-Gruppe"
            }
        ]
    }
}
```

## Fragenantworten

**GET:** `/api/audit/answers`

**Response:**
```json
{
   "data": {
        "answers": [
            {
                "id": 23,
                "audit_id": 1,
                "question_id": 2,
                "answer": "green",
                "comment": "",
                "description": "",
                "layer": 1,
                "group": "C-Gruppe"
            },
            {
                "id": 24,
                "audit_id": 1,
                "question_id": 22,
                "answer": "red",
                "comment": "notausgang blockiert durch kran",
                "description": "",
                "layer": 0,
                "group": "TN-Gruppe"
            }
        ]
    }
}
```

## Alle Audits abfragen

**GET:** `/api/audits/`

**Response:**
```json
{
   "data": {
        "audits:" [
            {
                "id": 1,
                "due_date": 2022-10-22T00:00:00.000Z,
                "duration": 10000,
                "recurrent_audit": true,
                "questions": [1, 4, 5, 2],
                "answers": [],
                "assigend_group": "C-Gruppe",
                "assigned_layer": 1,
                "auditor": 5,
                "created_by": 10,
                "audited_user": 12
            }
        ]
   }                             
}
```

## Geplante Audits / Rhytmus

**GET:** `/api/audit/planned/`

**Response:**
```json
{
   "data": {
        "audits": [
            {
                "title": "Von der Geschäftsführung in der TNL-Gruppe",
                "layer": 0,
                "recurrence_type": "monthly",
                "recurring_at": [
                    "Week1", 
                    "Week2"
                ]
                "number_questions": 2,
                "created_by": "Tony Stark"
            },
            {
                "title": "Von der Geschäftsführung in der C-Gruppe",
                "layer": 0,
                "recurrence_type": "monthly",
                "recurring_at": [
                    "Week1",
                    "Week4"
                ]
                "number_questions": 2,
                "created_by": "Tony Stark"
            },
        ]
    }
}
```

# Tasks 

## Aktuelle Aufgaben

**GET:** `/api/tasks`

**Antwort:**
Response Code: 200
```json
{
   "data": {
        "tasks": [
            {
                "icon_url": "/icons/lpa.png",
                "app_name": "Layered Process Audit",
                "title": "Spontaner Audit in der C-Gruppe",
                "paramters": [
                    "Layer 1",
                    2022-10-22T00:00:00.000Z
                ],
                "action": "/audit/42"
            }
        ]
    }
}
```
