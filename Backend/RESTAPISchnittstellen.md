In dieser Datei werden die angebotenen Schnittstellen der Services dokumentiert.

*Für eine genauere Beschreibung der Services siehe [Services.md](./Services.md)*

# User Management
Root-Verzeichnis: `api/user_management`

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
  "result": 1,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjozLCJleHBpcmVzIjoxNjcwODc0Mjc4LjM5MzI2MzYsImNvbXBhbnlfaWQiOjEsInJvbGUiOiJ3b3JrZXIifQ.tRwi3y1pvGre7sMrLgRA2j2_H0fhWHxhBuUeUtEWfCQ"
}
```

**Antwort (bei fehlgeschlagener login):**
Response Code: 401
```json
{
  "result": null,
  "token": None
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
    "result": 1,
    "first_name": "Michl",
    "last_name": "Baum"
}
```

## Register
**POST:** `/register`

```json
{
                "first_name": "Franz",
                "last_name": "Hans",
                "email": "franzhand@xzy.de",
                "password_hash": "test",
                "supervisor_id": 2,
                "layer_id": 1,
                "company_id": 1,
                "group_id": 1,
                "role_id": 1

            }
```

**Antwort:**

```json
{
  "result": 1,
  "id": 4,
  "first_name": "Franz",
  "last_name": "Hans"
}
```

**Antwort (wenn Email bereits existiert):**
HTTP Exception: 404
```json
{"detail": "Email already registered"}
```

## UserInfo abfragen
**GET:** `/user_id`

```json
{
    "result": 1,
    "data": [
        {
            "id": 2,
            "first_name": "Josef",
            "last_name": "Stahl",
            "email": "josef@test.de",
            "profile_picture_url": null,
            "role_id": 2,
            "group_id": 3,
            "supervisor_id": null,
            "layer_id": 3,
            "company_id": 1
        }
    ]
}
```

**Antwort:**

```json
{
    "result": 1,
    "data": {
        "supervisor_id": 2,
        "last_name": "Baum",
        "id": 3,
        "first_name": "Michl",
        "email": "michl@test.de",
        "profile_picture_url": null,
        "supervisorid": null,
        "supervisorlast_name": "Stahl",
        "supervisorfirst_name": "Josef",
        "company": {
            "id": 1,
            "company_name": "Failed Venture. INC"
        },
        "role": {
            "id": 1,
            "role_name": "worker"
        },
        "group": {
            "group_name": "QA",
            "company_id": 1,
            "id": 2
        },
        "layer": {
            "layer_name": "Office",
            "id": 2,
            "layer_number": 1,
            "company_id": 1
        }
    }
}
```

## JWT validieren
**POST:** `/validateJWT/`

**Antwort:**
```json
{
  "result": 1,
  "payload": {
    "user_id": 3,
    "expires": 1670874469.1393359,
    "company_id": 1,
    "role": "worker"
  }
}
```

**Antwort (bei fehlgeschlagener Validierung):**
Response Code: 401
```json
{
  "detail": "JWT not valid"
}
```

## Layer abfragen

**GET:** `/layers`
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

**Antwort:**
```json
{
    "result": 1,
    "data": [
        {
            "company_id": 1,
            "layer_number": 0,
            "id": 1,
            "layer_name": "Werkstatt",
            "company": {
                "id": 1,
                "company_name": "Failed Venture. INC"
            }
        },
        {
            "company_id": 1,
            "layer_number": 1,
            "id": 2,
            "layer_name": "Office",
            "company": {
                "id": 1,
                "company_name": "Failed Venture. INC"
            }
        },
    ]
}
```

## User einem Layer hinzufügen -> nur von Rolle "ceo" und "admin" erlaubt
**POST:** `/user/layer/<user_id>`

```json
{
    "layer": <layer_id>
}
```
**Antwort:**
```json
{
    "result": 1,
    "id": 3,
    "first_name": "Michl",
    "last_name": "Baum",
    "email": "michl@test.de",
    "profile_picture_url": null,
    "supervisor": {
        "supervisorid": null,
        "last_name": "Stahl",
        "first_name": "Josef"
    },
    "layer": {
        "layer_name": "Office",
        "id": 2,
        "layer_number": 1,
        "company_id": 1
    },
    "company": {
        "id": 1,
        "company_name": "Failed Venture. INC"
    },
    "group": {
        "group_name": "Fertigung",
        "id": 1,
        "company_id": 1
    },
    "role": {
        "id": 1,
        "role_name": "worker"
    }
}
```

**Antwort (bei Fehlschlag):**
HTTP Exception: 404
```json
{
    "detail": "No Permission"
}
```

## User einer Gruppe hinzufügen
**POST:** `/user/group/<user_id>`

```json
{
    "group": <group_id>
}
```

**Antwort:**

```json
{
    "result": 1,
    "id": 3,
    "first_name": "Michl",
    "last_name": "Baum",
    "email": "michl@test.de",
    "profile_picture_url": null,
    "supervisor": {
        "supervisorid": null,
        "last_name": "Stahl",
        "first_name": "Josef"
    },
    "layer": {
        "company_id": 1,
        "layer_number": 1,
        "layer_name": "Office",
        "id": 2
    },
    "company": {
        "id": 1,
        "company_name": "Failed Venture. INC"
    },
    "group": {
        "company_id": 1,
        "group_name": "QA",
        "id": 2
    },
    "role": {
        "id": 1,
        "role_name": "worker"
    }
}
```

## Layer hinzufügen
**POST:** `/layers`

```json
{
   "layer_name": "Werkstattebene",
   "layer_number": 1
}
```

**Antwort:**

```json
{
    "result": 1,
    "id": 5,
    "layer_name": "Sklaventreiber",
    "layer_number": 1,
    "company": {
        "id": 1,
        "company_name": "Failed Venture. INC"
    }
}
```

**Antwort (wenn Layer in der Firma schon existiert):**
HTTP Exception: 404
```json
{"detail": "Layer already exists in the Company"}
```

## Gruppe hinzufügen
**POST:** `/groups`

```json
{
   "group_name": "C-Gruppe"
}
```

**Antwort:**

```json
{
    "result": 1,
    "id": 4,
    "group_name": "Z-Promi",
    "company": {
        "id": 1,
        "company_name": "Failed Venture. INC"
    }
}
```

**Antwort (wenn Gruppe in der Firma schon existiert):**
HTTP Exception: 404
```json
{"detail": "Group already exists in the Company"}
```

## Alle Gruppen abrufen
**GET:** `/groups`

**Antwort:**
```json
{
    "result": 1,
    "data": [
        {
            "company_id": 1,
            "group_name": "Fertigung",
            "id": 1,
            "company": {
                "id": 1,
                "company_name": "Failed Venture. INC"
            }
        },
        {
            "company_id": 1,
            "group_name": "QA",
            "id": 2,
            "company": {
                "id": 1,
                "company_name": "Failed Venture. INC"
            }
        }
    ]
}
```

## Alle User in einem Layer abfragen
**GET:** `/group/<group_id>`

**Antwort:**
```json
{
    "result": 1,
    "data": [
        {
            "supervisor_id": 2,
            "last_name": "Baum",
            "id": 3,
            "first_name": "Michl",
            "email": "michl@test.de",
            "profile_picture_url": null,
            "company": {
                "id": 1,
                "company_name": "Failed Venture. INC"
            },
            "role": {
                "id": 1,
                "role_name": "worker"
            },
            "group": {
                "group_name": "QA",
                "company_id": 1,
                "id": 2
            },
            "layer": {
                "layer_name": "Office",
                "id": 2,
                "company_id": 1,
                "layer_number": 1
            }
        }
    ]
}
```

## alle Mitarbeiter von Audit Layer zurückgeben
**GET:** `/groups/employee/{group_id}/{audit_layer_id}`

**Antwort:**

```json
{
    "result": 1,
    "data": [
        {
            "supervisor_id": null,
            "last_name": "Stahl",
            "id": 2,
            "first_name": "Josef",
            "email": "josef@test.de",
            "profile_picture_url": null,
            "company": {
                "id": 1,
                "company_name": "Failed Venture. INC"
            },
            "role": {
                "id": 2,
                "role_name": "ceo"
            },
            "group": {
                "company_id": 1,
                "group_name": "Marketing",
                "id": 3
            },
            "layer": {
                "layer_name": "Geschäftsführung",
                "id": 3,
                "company_id": 1,
                "layer_number": 2
            }
        }
    ]
}
```

## Alle Supervisoren im Auditlayer von den User in einer Gruppe
**GET:** `/groups/supervisor/{audit_layer_id}`

**Antwort:**

```json
{
    "result": 1,
    "data": [
        {
            "supervisor_id": 2,
            "last_name": "Baum",
            "id": 3,
            "first_name": "Michl",
            "email": "michl@test.de",
            "profile_picture_url": null,
            "company": {
                "id": 1,
                "company_name": "Failed Venture. INC"
            },
            "role": {
                "id": 1,
                "role_name": "worker"
            },
            "group": {
                "group_name": "QA",
                "company_id": 1,
                "id": 2
            },
            "layer": {
                "layer_name": "Office",
                "id": 2,
                "company_id": 1,
                "layer_number": 1
            }
        }
    ]
}
```

## Alle Employees von dem Audit_layer in einer Gruppe
**GET:** `groups/employee/{group_id}/{audit_layer_id}`

**Antwort:**

```json
{
    "result": 1,
    "data": [
        {
            "supervisor_id": null,
            "last_name": "Stahl",
            "id": 2,
            "first_name": "Josef",
            "email": "josef@test.de",
            "profile_picture_url": null,
            "company": {
                "id": 1,
                "company_name": "Failed Venture. INC"
            },
            "role": {
                "id": 2,
                "role_name": "ceo"
            },
            "group": {
                "company_id": 1,
                "group_name": "Marketing",
                "id": 3
            },
            "layer": {
                "id": 3,
                "layer_name": "Geschäftsführung",
                "layer_number": 2,
                "company_id": 1
            }
        }
    ]
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
