*Für Beschreibung der Services siehe [Services.md](./Services.md)*

*Response vom Backend für Erfolg/Misserfolg der Operation wird nicht in diesem Dokument explizit mitaufgenommen, z.B. wenn eine Gruppe erstellt wird, wird das Backend zurückgeben, ob es funktioniert hat. Dies wird aber in diesem Dokuemnt nicht dargestellt*

# Glossar
- "Detail", bedeutet alle Daten in der Tabelle
- "Kompakt"/"Compact", bdeutet eine Übersicht aller wichtigen Daten, sowie Aggregierte Daten (z.B. Anzahl)
- "Status": Ob das Audit Grün, Geld oder Rot ist

# JWT Token
| Daten  | Veranwortlicher Service  |
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

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Email     | User Management                              |
| Passwort      |   User Management                            |
| (Firmenname)      |  User Management                             |
|  (URL zum Firmenname)     |  User Management                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

## Dashboard (Seite 2)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Aktuelle Aufgaben     |  Tasks                             |
| Freigeschaltete Apps / Lizenzen      |  *Aktuell out of scope*                             |


## Audit-Dashboard (Seite 3)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Analytics (z.B. Audit Score von Benutzer, Fragen des Audits, Layer und Gruppe zum Audit)    |   Audit                            |
| Offene Audits (z.B. `audits/open`)      |    Audit                           |
| Geplante Audits (z.B. `audits/planned`)      |  Audit                             |
|  Aufgaben     |    Tasks                           |

## Fragen (Seite 4)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Aufgaben     |  Tasks                             |
|  Frage (komplette Tabelle)     |   Audit                            |
|  Auswertung Fragenantworten (Anzahl Grün, Anzahl Gelb, Anzahl Rot), (z.B. bei Request auf `questions/compact`. Bei `questions/detail`, würde man Anwort mit der ganzen Tabelle bekommen)     |    Audit                           |

## Historie (Seite 5)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      |  User Management                             |
| Filter (Layer, Auditor, Status) |  Audit |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Aufgaben     |   Tasks                            |
|  Frage (komplette Tabelle)     |  Audit                             |
| Auswertung Fragenantworten (Anzahl Grün, Anzahl Gelb, Anzahl Rot) -> z.B. bei Request auf `questions/detail`      |   Audit                            |
| Audits  |   Audit                            |

## Auswertung (Seite 6)

#### Von Frontend zu Backend

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  JWT Token     | User Management                              |
| Filterung: Monat, Sortierung (z.B. Fragenanzahl absteigend), Pagination (Seitennummer)      |   Audit                            |


#### Von Backend zu Frontend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| Analytics über Audits      |   Audit                            |
|  Fragen (Details)     |   Audit                            |
|  Aufgaben     |   Tasks                            |

## Konfiguration (Seite 7)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Ebenen     |  User Management                             |
| Gruppen zu jeder Ebene      |  User Management                             |
|  Aufgaben     |   Tasks                            |

## Konfiguration - 1 (Seite 8, Gruppenverwaltung)

#### Von Frontend zu Backend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      |  User Management                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Gruppen     |  User Management                             |
| Mitglieder der Gruppen      | User Management                              |

## Konfiguration - 2 (Seite 9, Dark Mode)

Kein Datenaustausch (evtl. Settings Update)

## Konfiguration_hierarchie_hinzufügen (Seite 10)

#### Von Frontend zu Backend
1. GET:

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| Firmenname      |  User Management                             |

-> Um die Layer zu bekommen für Dropdown (optional, wenn die Layer nicht bereits zwischengespeichert sind für "Konfiguration - 1")

2. POST:

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      |  User Management                             |
| Layer     |  User Management                             |
| Name     |  User Management                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Layer (wenn angefragt)     |  User Management                             |

## Konfiguration_Gruppe_hinzufügen (Seite 11)

**POST:**

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      |  User Management                             |
| Gruppenname     |  User Management                             |

#### Von Backend zu Frontend

*Nichts*

## Audit erstellen (Seite 12)

#### Von Frontend zu Backend
1. GET
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      | User Management                              |

2. POST

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      | User Management                              |
| Ausgewähltes Layer      |    Audit                           |
| Ausgewählte Gruppe      |    Audit                           |
|  Ausgewählte Fragen     |  Audit                             |

#### Von Backend zu Frontend

Antwort auf GET:

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Layer     | User Management                              |
| Gruppen      |  User Management                             |
| Fragen      |  Audit                             |

## Historie zugeklappt (Seite 13)

*Genau das selbe wie bei Historie (Seite 5)*

#### Von Frontend zu Backend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      |  User Management                             |
| Pagination, Filterung (z.B. Layer)      |  Audit                             |

#### Von Backend zu Frontend
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| Audits      |  Audit                             |
| Fragen (Detail)      |   Audit                            |

## Fragen neue Frage (Seite 14)

#### Von Frontend zu Backend

1. GET
| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  JWT Token     |  User Management                             |
|  Ausgewähltes Layer (damit man die möglichen Gruppen herausfindet)     |  User Management                             |
|  Ausgewählte Gruppe (damit man die möglichen Kategorien herausfindet)     |  User Management   |

2. POST

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  JWT Token     |  User Management                             |
| ID von der ausgewählten Frage, falls Frage bearbeitet wird      |  Audit                             |
| Neuer Titel      |  Audit                             |
|  Neue Beschreibung     |  Audit                             |
| Neuer Layer      |     Audit                          |
|  Neue Gruppe     | Audit                              |
| Neue Kategorie      |  Audit                             |

#### Von Backend zu Frontend

Bei GET: 

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| Ebenen      |   User Management                            |
|  Gruppen     | User Management                              |
| Kategorien      |  User Management                             |

## Konfiguration_Hierarchie_Gruppe_hinzufügen (Seite 15)

#### Von Frontend zu Backend

1. GET (optional, wenn nicht abgespeichert wurde, damit das Dropdown mit "Gruppen" befüllt werden kann):

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  JWT Token     |  User Management                             |

2. POST:

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  JWT Token     |  User Management                             |
|  Gruppe     |  Audit                             |
|  Fragenanzahl     |  Audit                             |
|  Rhytmus     |  Audit                             |
|  Tage/Wochen/Monate     |  Audit                             |

#### Von Backend zu Frontend

Beim GET:

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Gruppen     |  User Management                             |

## Konfiguration_Gruppe_Mitglieder_hinzufügen (Seite 16)

#### Von Frontend zu Backend

1. GET

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  JWT Token     |  User Management                             |

2. POST

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  JWT Token     |  User Management                             |
|  Mitglied     |  User Management                             |
|  Basislayer (ja/nein)     |  User Management                             |
|  Gruppe     |  User Management                             |

#### Von Backend zu Frontend

Beim GET:

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  User der Firma     |  User Management                             |

## Audit durchführen (Seite 17)

#### Von Frontend zu Backend

*GET:*

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      | User Management                              |

*POST (beim Abschließen):*

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| JWT Token      | User Management                              |
|  Audit ID    | Audit                              |
| Wenn "Abschließen" Button gedrückt: Audit ID, Fragenantwort, Fragen ID, Dauer      |     Audit                          |

#### Von Backend zu Frontend

*Beim GET:*

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
| Audit (Detail)      |  Audit                             |
| Fragen des Audits (Detail)      |   Audit                            |

## Historie Details (Seite 18)

#### Von Frontend zu Backend

*GET:*

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  JWT Token     |  User Management                             |
| Audit ID      |   Audit                            |

#### Von Backend zu Frontend

*Antwort auf GET:*

| Daten | Verantwortlicher Service |
|-------|-------------------------------|
|  Fragen (Detail)     |   Audit                            |

## Audit durchführen Frage beantworten (Seite 19)

Unwichtig für Backend, da Daten erst bei "Abschluss" zum Backend geschickt wird (vgl. Audit durchführen übersicht, Seite 13)