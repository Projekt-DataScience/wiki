*Für Beschreibung der Microservices siehe [Microservices.md](./Microservices.md)*

# Glossar
- "Detail", bedeutet alle Daten in der Tabelle
- "Kompakt"/"Compact", bdeutet eine Übersicht aller wichtigen Daten, sowie Aggregierte Daten (z.B. Anzahl)

# JWT Token
| Daten  | Veranwortlicher Microservice  |
|---|---|
| Vorname  | User Management  |
| Nachname | User Management  |
| Firmenname | User Management  |
| (URL zum Profilbild) | User Management  |
| Email  | User Management  |
| Rolle  | User Management  |
| Fälligkeitsdatum der Session  |User Management   |
| SessiondId  | User Management  |

# Benötigte Daten pro View
Views aus [diesem Mockup](https://xd.adobe.com/view/63b68c34-69a2-4318-9bb5-3f2ab5062958-36e5/)

## Login (Seite 1)

#### Von Frontend zu Backend

| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  Email     | User Management                              |
| Passwort      |   User Management                            |
| (Firmenname)      |  User Management                             |
|  (URL zum Firmenname)     |  User Management                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

## Dashboard (Seite 2)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend

| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  Aktuelle Aufgaben     |  Tasks                             |
| Freigeschaltete Apps / Lizenzen      |  *Aktuell out of scope*                             |


## Audit-Dashboard (Seite 3)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend

| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  Analytics (z.B. Audit Score von Benutzer, Fragen des Audits, Layer und Gruppe zum Audit)    |   Audit                            |
| Offene Audits (z.B. `audits/open`)      |    Audit                           |
| Geplante Audits (z.B. `audits/planned`)      |  Audit                             |
|  Aufgaben     |    Tasks                           |

## Fragen (Seite 4)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  Aufgaben     |  Tasks                             |
|  Frage (komplette Tabelle)     |   Audit                            |
|  Auswertung Fragenantworten (Anzahl Grün, Anzahl Gelb, Anzahl Rot), (z.B. bei Request auf `questions/compact`. Bei `questions/detail`, würde man Anwort mit der ganzen Tabelle bekommen)     |    Audit                           |

## Historie (Seite 5)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  Aufgaben     |   Tasks                            |
|  Frage (komplette Tabelle)     |  Audit                             |
| Auswertung Fragenantworten (Anzahl Grün, Anzahl Gelb, Anzahl Rot) -> z.B. bei Request auf questions/detail`      |   Audit                            |

## Auswertung

#### Von Frontend zu Backend

| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  JWT Token     | User Management                              |
| Filterung: Monat, Sortierung (z.B. Fragenanzahl absteigend), Pagination (Seitennummer)      |   Audit                            |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| Analytics über Audits      |   Audit                            |
|  Fragen (Details)     |   Audit                            |

## Konfiguration (Seite 7)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  Ebenen     |  User Management                             |
| Gruppen zu jeder Ebene      |  User Management                             |

## Konfiguration - 1 (Seite 8, Gruppenverwaltung)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  Gruppen     |  User Management                             |
| Mitglieder der Gruppen      | User Management                              |

## Konfiguration - 2 (Seite 9, Dark Mode)

Kein Datenaustausch (evtl. Settings Update)

## Audit erstellen (Seite 10)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| JWT Token      | User Management                              |
| Ausgewähltes Layer      |    Audit                           |
| Ausgewählte Gruppe      |    Audit                           |
|  Ausgewählte Fragen     |  Audit                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  Layer     | User Management                              |
| Gruppen      |  User Management                             |
| Fragen      |  Audit                             |

## Historie zugeklappt (Seite 11)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| JWT Token      |  User Management                             |
| Pagination, Filterung (z.B. Layer)      |  Audit                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| Audits      |  Audit                             |
| Fragen (Detail)      |   Audit                            |

## Fragen neue Frage (Seite 12)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  JWT Token     |  User Management                             |
| ID von der ausgewählten Frage, falls Frage bearbeitet wird      |  Audit                             |
| Neuer Titel      |  Audit                             |
|  Neue Beschreibung     |  Audit                             |
| Neuer Layer      |     Audit                          |
|  Neue Gruppe     | Audit                              |
| Neue Kategorie      |  Audit                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| Ebenen      |   User Management                            |
|  Gruppen     | User Management                              |
| Kategorien      |  User Management                             |

## Audit durchführen

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| JWT Token      | User Management                              |
|  Audit ID    | Audit                              |
| Wenn "Abschließen" Button gedrückt: Audit ID, Fragenantwort, Fragen ID, Dauer      |     Audit                          |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
| Audit (Detail)      |  Audit                             |
| Fragen des Audits (Detail)      |   Audit                            |

## Historie Details

#### Von Frontend zu Backend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  JWT Token     |  User Management                             |
| Audit ID      |   Audit                            |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Microservice |
|-------|-------------------------------|
|  (Fragen (Detail)), weil evtl. wird das bereits im Frontend zwischengespeichert, denn die Fragen werden bereits bei der Historie zugeklappt (Seite 11) geladen     |   Audit                            |

## Audit durchführen Frage beantworten

Unwichtig für Backend, da Daten erst bei "Abschluss" zum Backend geschickt wird (vgl. Audit durchführen übersicht, Seite 13)