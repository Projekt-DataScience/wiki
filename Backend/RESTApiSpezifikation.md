# Glossar
- "Detail", bedeutet alle Daten in der Tabelle
- "Kompakt"/"Compact", bdeutet eine Übersicht aller wichtigen Daten, sowie Aggregierte Daten (z.B. Anzahl)

# JWT Token
- Vorname
- Nachname
- (URL zum Profilbild)
- Email
- Rolle
- Fälligkeitsdatum der Session
- SessiondId

# Benötigte Daten pro View
Views aus [diesem Mockup](https://xd.adobe.com/view/63b68c34-69a2-4318-9bb5-3f2ab5062958-36e5/)

## Login (Seite 1)

#### Von Frontend zu Backend
- Email
- Passwort
- (Firmenname)
- (URL zum Firmenname)
- (CSRF Token)

#### Von Backend zu Frontend
- JWT Token

## Dashboard (Seite 2)

#### Von Frontend zu Backend
- JWT Token

#### Von Backend zu Frontend
- Aktuelle Aufgaben (evlt. über eigenen MS)
- Freigeschaltete Apps / Lizenzen (evlt. über eignene MS)
- Vorname
- Nachname
- (URL zum Profilbild)
- Firmenname
- (URL zum Firmenlogo)

## Audit-Dashboard (Seite 3)

#### Von Frontend zu Backend
- JWT Token

#### Von Backend zu Frontend
- Firmenname
- Vorname
- Nachname
- Rechte / Rolle
- (URL zum Profilbild)
- Analytics (z.B. Audit Score von Benutzer, Fragen des Audits, Layer und Gruppe zum Audit)
- Offene Audits -> `audits/open`
- Geplante Audits -> `audits/planned`
- Aufgaben

## Fragen (Seite 4)

#### Von Frontend zu Backend
- JWT Token

#### Von Backend zu Frontend
- Firmenname
- Aufgaben
- Frage (komplette Tabelle)
- Auswertung Fragenantworten (Anzahl Grün, Anzahl Gelb, Anzahl Rot) -> z.B. bei Request auf `questions/compact`. Bei `questions/detail`, würde man Anwort mit der ganzen Tabelle bekommen

## Historie (Seite 5)

#### Von Frontend zu Backend
- JWT Token

#### Von Backend zu Frontend
- Firmenname
- Aufgaben
- Frage (komplette Tabelle)
- Auswertung Fragenantworten (Anzahl Grün, Anzahl Gelb, Anzahl Rot) -> z.B. bei Request auf questions/detail`

## Auswertung

#### Von Frontend zu Backend
- JWT Token
- Filterung: Monat, Sortierung (z.B. Fragenanzahl absteigend), Pagination (Seitennummer)

#### Von Backend zu Frontend
- Analytics über Audits
- Fragen (Details)

## Konfiguration (Seite 7)

#### Von Frontend zu Backend
- JWT Token

#### Von Backend zu Frontend
- Ebenen
- Gruppen zu jeder Ebene

## Konfiguration - 1 (Seite 8, Gruppenverwaltung)

#### Von Frontend zu Backend
- JWT Token

#### Von Backend zu Frontend
- Gruppen
- Mitglieder der Gruppen

## Konfiguration - 2 (Seite 9, Dark Mode)

Kein Datenaustausch (evtl. Settings Update)

## Audit erstellen (Seite 10)

#### Von Frontend zu Backend
- JWT Token
- Ausgewähltes Layer
- Ausgewählte Gruppe
- Ausgewählte Fragen

#### Von Backend zu Frontend
- Layer
- Gruppen
- Fragen

## Historie zugeklappt (Seite 11)

#### Von Frontend zu Backend
- JWT Token
- Pagination, Filterung (z.B. Layer)

#### Von Backend zu Frontend
- Audits
- Fragen (Detail)

## Fragen neue Frage (Seite 12)

#### Von Frontend zu Backend
- JWT Token
- ID von der ausgewählten Frage, falls Frage bearbeitet wird
- Neuer Titel
- Neue Beschreibung
- Neuer Layer
- Neue Gruppe
- Neue Kategorie

#### Von Backend zu Frontend
- Ebenen
- Gruppen
- Kategorien

## Audit durchführen

#### Von Frontend zu Backend
- JWT Token
- Audit ID
- Wenn "Abschließen" Button gedrückt: Audit ID, Fragenantwort, Fragen ID, Dauer

#### Von Backend zu Frontend
- Audit (Detail)
- Fragen des Audits (Detail)

## Historie Details

#### Von Frontend zu Backend
- JWT Token
- Audit ID

#### Von Backend zu Frontend
- (Fragen (Detail)), weil evtl. wird das bereits im Frontend zwischengespeichert, denn die Fragen werden bereits bei der Historie zugeklappt (Seite 11) geladen

## Audit durchführen Frage beantworten

Unwichtig für Backend, da Daten erst bei "Abschluss" zum Backend geschickt wird (vgl. Audit durchführen übersicht, Seite 13)