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

## User einem Layer hinzufügen
**POST:** `/api/user/layer/<user_id>`

```json
{
    "layer": <layer_id>
}
```

**Response:**
`kompletter user model, ohne password hash`

## User einer Gruppe hinzufügen
**POST:** `/api/user/group/<user_id>`

```json
{
    "group": <group_id>
}
```

**Response:**
`kompletter user model, ohne password hash`

## Layer hinzufügen
**POST:** `/api/layers`

```json
{
   "layer_name": "Werkstattebene",
   "layer_number": 1
}
```

**Response:**

```json
{
    "id": 123,
    "layer_name": "Werkstattebene",
    "layer_number": 1
}
```

## Gruppe hinzufügen
**POST:** `/api/groups`

```json
{
   "group_name": "C-Gruppe"
}
```

**Response:**

```json
{
    "id": 12,
   "group_name": "C-Gruppe"
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

## Alle User in einem Layer abfragen
**GET:** `/api/groups/<group_id>`

**Response:**
```json
{
   "data": {
        "group_id": <group_id>
        "users": [
            {
                "id": 1,
                "first_name": "Tony",
                "last_name": "Start",
                "layer": 2,
                "supervisor": <supervisor_id>,
                "email": "tony.start@company.com",
                "profile_picture": "https://images.project-datascience.com/f8e579fc-bfc7-44a2-914e-3d706a01c7d8.png"
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
                "due_date": "2022-10-22T00:00:00.000Z",
                "created_by": "Tony Stark"
            },
            {
                "title": "Spontaner Audit in der TN-Grupe",
                "layer": 1,
                "due_date": "2022-10-22T00:00:00.000Z",
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

## Frage erstellen
**POST:** `/api/question`

```json
{
    "layer": <layer_id>,
    "question": "asdf asdfasdf asd?",
    "description": "asdfasdfj klsadjfaklsdfjaölsdk fjasdlöf asdf",
    "category": "Qualitätssicherung",
    "group": <group_id>,
    "layer": <layer_id>
}
```

**Response:**

```json
{
    "id": 55,
    "layer": <layer_id>,
    "question": "asdf asdfasdf asd?",
    "description": "asdfasdfj klsadjfaklsdfjaölsdk fjasdlöf asdf",
    "category": "Qualitätssicherung",
    "group": <group_id>,
    "layer": <layer_id>
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

## Neues (spontanes) Audit erstellen

**POST:** `/api/audits`

```json
{
    "due_date": "2022-10-22T00:00:00.000Z",
    "auditor": <user_id>,
    "assigned_group": <group_id>,
    "assigned_layer": <layer_id>,
    "question_count": 2
}
```

**Response:**

```json
{
    "due_date": "2022-10-22T00:00:00.000Z",
    "auditor": <user_id>,
    "assigned_group": <group_id>,
    "assigned_layer": <layer_id>,
    "created_by": <user_id>,
    "duration": None,
    "reccurent_audit": false,
    "lpa_questions: [
        {"question": "ajlskdf askjf öasld fj?", "description": "asdfasdfasdfsdf", "id": 12, category: "Qualitätssicherung"},
        {"question": "asdf asdf asdf asd?", "description": "asdfasdf", "id": 2, category: "Qualitätssicherung"},
    ]
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
                "due_date": "2022-10-22T00:00:00.000Z",
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

## Audit durchführen


**POST:** `/api/audit/<audit_id>`

```json
{
    "answers": [
        {"question": <question_id>, "answer": 0, "comment": "asdfasdf asdf sdf", "reasone": "asdfasdfadsfasd"},
        {"question": <question_id>, "answer": 2, "comment": "", "reason": ""},
    ],
    "duration": 120
}
```

**Response:**
*Kompletter audit mit allen questions und answers*

## Geplantes Audit / Rhytmus / Reccurence erstellen

**POST:** `/api/audit/planned`

```json
{
    "auditor": <user_id>,
    "group": <group_id>,
    "layer": <layer_id>,
    "question_count": 5,
    "recurrence_type": "weekly",
    "value": [
        "monday",
        "wednesday"
    ]
}
```

**Response:**

```json
{
    "id": 22,
    "auditor": <user_id>,
    "group": <group_id>,
    "layer": <layer_id>,
    "question_count": 5,
    "recurrence_type": "weekly",
    "value": [
        "monday",
        "wednesday"
    ]
}
```

## Geplante Audits / Rhytmus abfragen

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
  "tasks": [
        {
          "icon": "lpa",
          "app_name": "Layered Process Audit",
          "title": "Spontaner Audit in der C-Gruppe",
          "date": "2022-10-22T00:00:00.000Z",
          "parameter": "Layer 1",
          "id": <audit id>
        },
        {
          "icon": "lpa",
          "app_name": "Layered Process Audit",
          "title": "Spontaner Audit in der D-Gruppe",
          "date": "2023-10-22T00:00:00.000Z",
          "parameter": "Layer 2",
          "id": <audit id>
        }
      ]
}
```
