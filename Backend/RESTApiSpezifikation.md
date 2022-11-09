# Glossar
- "Detail", bedeutet alle Daten in der Tabelle
- "Kompakt"/"Compact", bdeutet eine Übersicht aller wichtigen Daten, sowie Aggregierte Daten (z.B. Anzahl)

# JWT Token
- Vorname
- Nachname
- Firmenname
- (URL zum Profilbild)
- Email
- Rolle
- Fälligkeitsdatum der Session
- SessiondId

-> User Management MS / Login MS

# Benötigte Daten pro View
Views aus [diesem Mockup](https://xd.adobe.com/view/63b68c34-69a2-4318-9bb5-3f2ab5062958-36e5/)

## Login (Seite 1)

#### Von Frontend zu Backend
- Email -> User Management MS
- Passwort -> User Management MS
- (Firmenname)
- (URL zum Firmenname)
- (CSRF Token)

#### Von Backend zu Frontend
- JWT Token -> User Management MS

## Dashboard (Seite 2)

#### Von Frontend zu Backend
- JWT Token -> User Management MS

#### Von Backend zu Frontend
- Aktuelle Aufgaben -> Tasks MS
- Freigeschaltete Apps / Lizenzen (evlt. über eignene MS)
- Vorname -> User Management MS
- Nachname -> User Management MS
- (URL zum Profilbild) -> User Management MS
- Firmenname -> Organisation Management
- (URL zum Firmenlogo) -> User Management MS

## Audit-Dashboard (Seite 3)

#### Von Frontend zu Backend
- JWT Token -> User Management MS

#### Von Backend zu Frontend
- Firmenname -> User Management MS
- Vorname -> User Management MS
- Nachname -> User Management MS
- Rechte / Rolle -> User Management MS
- (URL zum Profilbild) -> User Management MS
- Analytics (z.B. Audit Score von Benutzer, Fragen des Audits, Layer und Gruppe zum Audit)
- Offene Audits (z.B. `audits/open`) -> Audit MS
- Geplante Audits (z.B. `audits/planned`) -> Audit MS
- Aufgaben -> Tasks MS

## Fragen (Seite 4)

#### Von Frontend zu Backend
- JWT Token -> User Management MS

#### Von Backend zu Frontend
- Firmenname -> User Management MS
- Aufgaben -> Tasks MS
- Frage (komplette Tabelle) -> Audit MS 
- Auswertung Fragenantworten (Anzahl Grün, Anzahl Gelb, Anzahl Rot), (z.B. bei Request auf `questions/compact`. Bei `questions/detail`, würde man Anwort mit der ganzen Tabelle bekommen) -> Audit MS

## Historie (Seite 5)

#### Von Frontend zu Backend
- JWT Token -> User Management MS

#### Von Backend zu Frontend
- Firmenname -> User Management MS
- Aufgaben -> Tasks MS
- Frage (komplette Tabelle) -> Audit MS
- Auswertung Fragenantworten (Anzahl Grün, Anzahl Gelb, Anzahl Rot) -> z.B. bei Request auf questions/detail` -> Audit MS

## Auswertung

#### Von Frontend zu Backend
- JWT Token -> User Management MS
- Filterung: Monat, Sortierung (z.B. Fragenanzahl absteigend), Pagination (Seitennummer) -> Audit MS

#### Von Backend zu Frontend
- Analytics über Audits -> Audit MS
- Fragen (Details) -> Audit MS

## Konfiguration (Seite 7)

#### Von Frontend zu Backend
- JWT Token -> User Management MS

#### Von Backend zu Frontend
- Ebenen -> User Management MS
- Gruppen zu jeder Ebene -> User Management MS

## Konfiguration - 1 (Seite 8, Gruppenverwaltung)

#### Von Frontend zu Backend
- JWT Token -> User Management MS

#### Von Backend zu Frontend
- Gruppen -> User Management MS
- Mitglieder der Gruppen -> User Management MS

## Konfiguration - 2 (Seite 9, Dark Mode)

Kein Datenaustausch (evtl. Settings Update)

## Audit erstellen (Seite 10)

#### Von Frontend zu Backend
- JWT Token -> User Management MS
- Ausgewähltes Layer -> Audit MS
- Ausgewählte Gruppe -> Audit MS
- Ausgewählte Fragen -> Audit MS

#### Von Backend zu Frontend
- Layer -> User Management MS
- Gruppen -> User Management MS
- Fragen -> Audit MS

## Historie zugeklappt (Seite 11)

#### Von Frontend zu Backend
- JWT Token -> User Management MS
- Pagination, Filterung (z.B. Layer) -> Audit MS

#### Von Backend zu Frontend
- Audits -> Audit MS
- Fragen (Detail) -> Audit MS

## Fragen neue Frage (Seite 12)

#### Von Frontend zu Backend
- JWT Token -> User Management MS
- ID von der ausgewählten Frage, falls Frage bearbeitet wird -> Audit MS
- Neuer Titel -> Audit MS
- Neue Beschreibung -> Audit MS
- Neuer Layer -> Audit MS
- Neue Gruppe -> Audit MS
- Neue Kategorie -> Audit MS

#### Von Backend zu Frontend
- Ebenen -> User Management MS
- Gruppen -> User Management MS
- Kategorien -> User Management MS

## Audit durchführen

#### Von Frontend zu Backend
- JWT Token -> User Management MS
- Audit ID -> Audit MS
- Wenn "Abschließen" Button gedrückt: Audit ID, Fragenantwort, Fragen ID, Dauer -> Audit MS

#### Von Backend zu Frontend
- Audit (Detail) -> Audit MS
- Fragen des Audits (Detail) -> Audit MS

## Historie Details

#### Von Frontend zu Backend
- JWT Token -> User Management MS
- Audit ID -> Audit MS

#### Von Backend zu Frontend
- (Fragen (Detail)), weil evtl. wird das bereits im Frontend zwischengespeichert, denn die Fragen werden bereits bei der Historie zugeklappt (Seite 11) geladen -> Audit MS

## Audit durchführen Frage beantworten

Unwichtig für Backend, da Daten erst bei "Abschluss" zum Backend geschickt wird (vgl. Audit durchführen übersicht, Seite 13)