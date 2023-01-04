Projekt: Data Science in der industriellen Produktion

**Auftraggeber:**\
   HWH GmbH

**Auftragnehmer:**\
   Projektgruppe WS22/23 "Data Science in der industriellen Produktion"
   *Fabian Hueber (fabiancedrik.hueber@stud.hs-kempten.de)*
   *Fabio D'Angelo (fabio.dangelo@stud.hs-kempten.de)*
   *Jonas Mildner (jonas.mildner@stud.hs-kempten.de)*
   *Raphael Seliger (raphaelmanuel.seliger@stud.hs-kempten.de)*
   *Sandro Berger (sandro.berger@stud.hs-kempten.de)*
   *Fahri Korkmaz (fahri.korkmaz@stud.hs-kempten.de)*
   
# Versionen
Für genauere Änderungshistorie, siehe Git-History.

| **Version**  | **Datum**   | **Kommentar**   |**Status**  |
|------------- |-----------  |---------------- |------------|
| 0.1          | 27.10.2022    | Grundstruktur erstellt   |draft     |



# Inhaltsverzeichnis

- [Zielbestimmung](#zielbestimmung)
    - [Musskriterien](#musskriterien)
    - [Wunschkriterien](#wunschkriterien)
    - [Abgrenzungskriterien](#abgrenzungskriterien)
- [Produkteinsatz](#produkteinsatz)
    - [Anwendungsbereich](#anwendungsbereich)
    - [Glossar](#glossar)
    - [Zielgruppen](#zielgruppen)
    - [Betriebsbedingungen](#betriebsbedingungen)
- [Funktionale Anforderungen](#funktionale-anforderungen)
    - [Übersicht](#übersicht)
    - [Detailbeschreibung Use-Cases](#detailbeschreibung-use-cases)
    - [Offene Punkte](#offene-punkte)
- [Produkteigenschaften](#produkteigenschaften)
    - [Systemumgebung](#systemumgebung)
    - [Benutzbarkeit](#benutzbarkeit)
    - [Effizienz](#effizienz)
    - [Wartbarkeit und Portierung](#wartbarkeit-und-portierung)
    - [Sicherheitsanforderungen](#sicherheitsanforderungen)
    - [Normen und gesetzliche Anforderungen](#normen-und-gesetzliche-anforderungen)
- [Produktdaten](#produktdaten)
- [Ergänzungen](#ergänzungen)

# Zielbestimmung

## Musskriterien

Hier werden alle Kriterien beschreiben, die das Produkt können muss,
damit es für den vorgegebenen Einsatzzweck verwendet werden kann.

#### Nutzer
- Einloggen in die Web Applikation
- Ausloggen aus der Web Applikation
- Anzeige von Apps
- Auswahl von Apps
- Anzeige relevanter Fragen, während eines zugewiesenen Audits
- Beantwortung von Audit-Fragen mit den rot, gelb und grün
- Hinzufügen eines Kommentar, wenn eine Audit-Frage mit rot beantwortet wurde
- Anzeige einer Übersicht mit zugewiesenen Audits
- Anlegen von spontanen Audits: Anzahl der Fragen festlegen, Ebene zuordnen

#### Prüfer
- Audits einsehen und Statistiken zu den Audits ansehen
- Anlegen und Löschen von Fragen
- Anzeige einer Übersicht von Fragen
- Zuweisen an Audits an Nutzer

#### Firmenchef
- Hinzufügen von hierarchischen Ebenen
- Zuweisen von Gruppen zu hierarchischen Ebenen

## Wunschkriterien
Hier werden alle Kriterien beschrieben, die das Produkt können sollte,
um die Wünsche an das zu entwickelnde Produkt so gut wie möglich zu erfüllen.

#### Nutzer
- Account verwalten: Passwort, Vorname, Nachname

#### Administrator
- Anlegen von Firmen
- Löschen von Firmen

#### Firmenchef
- Anlegen von Nutzern

## Abgrenzungskriterien

Folgende Ziele werden bei dem neuen Produkt bewusst **nicht** verfolgt:

- Anforderungen aus dem Lastenheft, die zum Implementieren der Layered Process Audit (LPA) Funktionalität nicht notwendig sind
- Es werden nur vereinfachte Hierarchielayer abgebildet in der ersten Version, keine Basislayer
- Es werden in der ersten Version nur spontane, keine geplanten Audits umgesetzt

# Produkteinsatz

Dieses Produkt wird für die Firma HWH entwickelt, die Ihren Kunden eine Plattform bietet möchte, um unterschiedliche Applikationen zu nutzen.
Hierfür wird beispielhaft eine Applikation bereitgestellt, die es Kunden ermöglicht Layered Process Audits in Ihren Unternehmen durchzuführen.
Die entwickelte Software soll als Open Source Projekt für jeden Interessierten zugänglich gemacht werden. 

## Anwendungsbereich

## Glossar

## Zielgruppen

## Betriebsbedingungen

# Funktionale Anforderungen

## Übersicht

Im nachfolgenden Diagramm sind alle Use Cases, Nutzer und Beziehungen zwischen diesen abgebildet.

## User-Stories

**Nutzer**
- Als Nutzer möchte ich mich in die Web- Applikation einloggen können, sodass meine Daten sicher sind. 
- Als Nutzer möchte ich eine Übersicht der für mich nutzbaren / freigeschalteten Apps sehen und eine ausgewählte App starten können.
- Als Nutzer möchte ich mich ausloggen können.
- Als Nutzer sollen mir während des zugewiesenen Audits relevante Fragen gestellt werden.
- Als Nutzer möchte ich die Fragen mit rot, gelb, grün beantworten und bei rot einen Kommentar hinzufügen können.
- Als Nutzer möchte ich eine Übersicht meiner zugewiesenen Audits sehen.

**Prüfer**
- Als Prüfer möchte ich die Ergebnisse der Audits einsehen können. Die Ergebnisse sollen auch in einer Statistik aufbereitet werden.
- Als Prüfer möchte ich Fragen anlegen oder löschen und eine Übersicht über die Fragen sehen können.
- Als Prüfer möchte ich spontane Audits anlegen, die Anzahl der Fragen festlegen und einer Ebene zuordnen können.

**Firmenchef**
- Als Firmenchef kann ich hierarchische Ebenen hinzufügen und diesen Ebenen bestimmte Gruppen zuweisen.
- Als Firmenchef möchte ich die Funktionen und Ansichten eines Prüfers verwenden können.

## Detailbeschreibung Use-Cases

## Offene Punkte

# Produkteigenschaften

## Systemumgebung

Hardwareumgebung

**Softwareumgebung**  
- Container-Engine: Docker, Docker-Compose
- Authentifizierung mittels JWT Tokens

# Nicht-funktionale Anforderungen
Die Nicht-funktionalen Anforderungen wurden nach der ISO 25010 formuliert.

## Benutzbarkeit

**Optimale Erkennbarkeit:**
  - Das Design der Benutzeroberfläche sollte Barrierefrei gestaltet sein

**Erlernbarkeit:**
  - Die Benutzeroberfläche sollte so intuitiv wie möglich gestaltet werden (Optional nach Normen "IEC 62366-1:2015" bzw. "FDA Human Factors Guidances")
  - Unklare Bedienungsmöglichkeiten sollten erklärt werden

**Ästhetisches User-Interface:**
  - Die Benutzeroberfläche sollte modern und ansprechend gestaltet werden (Optional nach Designsystemen wie dem Material UI Design)

## Wartbarkeit und Portierbarkeit

**Modularer Aufbau**
  - Das Frontend soll modular aufgebaut werden, um die Anbindung weiterer Anwendungen zu erleichtern
  - Backend sollte in verschiedene Module aufgeteilt werden, welche unabhängig voneinander laufen und erweitert werden können

**Gute Adaptivität**
  - Der Code des Frontends/Backends sollte einfach wartbar und abänderbar sein
  - Im Backend sollten so wenig verschiedene Technologien wie nötig verwendet werden (z.B. keine 10 verschiedene Backendframeworks, wenn es nicht nötig ist)
  - Es sollten standardisierte Technologien verwendet werden, z.B.: REST, JSON, JWT
  - Die standardmäßigen Konventionen und Projektstrukturen der Frameworks sollten nach Möglichkeit nicht verändert werden

**Wiederverwendbare Komponenten**
  - Das Frontend soll aus wiederverwendbaren Komponenten aufgebaut werden

**Skalierbarkeit**
  - Das Backend und Frontend sollte skalierbar sein

**Installierbarkeit**
- Es sollte möglich sein, dass das Backend sowie Frontend sowohl in der Cloud als auch On-Premise läuft
- Es sollte eine Bedienungsanleitung zum deployen des Backends erstellt werden

**Gute Analyse-Funktion**
- Das Backend sowie Frontend sollte mittels der Versionsverwaltungssoftware "Git" versioniert werden

## Effizienz

**Zeitverhalten**
  - Der Nutzer sollte nicht unverhältnissmäßig lange auf Antworten des Systems warten müssen

**Ressourcenverbrauch**
  - Der Ressourcenverbrauch des Systems muss überschaubar sein

## Sicherheitsanforderungen

**Datenschutz**
  - Die Verarbeitung der Benutzerdaten muss nach aktuellen Datenschutzbestimmungen erfolgen (DSGVO-Konform)

**Sichere Administration und Benutzeraccounts**
  - Die Benutzeroberfläche muss durch einen Login gesichert werden
  - Es soll über HTPPS mit einem potenziellen Server kommuniziert werden

**Integrität und Sicherheit**
  - Die Datensicherheit und Integrität soll gewährleistet werden
  - Das Backend sollte sicher vor typischen Web Applikationsschwachstellen sein (OWASP Top 10)

## Verlässlichkeit

**Ausgereifte Softwarequalität**
  - Es soll auf Namenskonventionen geachtet werden
  - Es soll auf eine gute Lesbarkeit und Dokumentation des Codes geachtet werden

# Produktdaten
Welche Benutzerdaten speichert das System?

## User
- UserId
- Vorname
- Nachname
- Email
- Passwort
- GruppeId
- Rechte / Rolle

## Ebene
- EbenenId
- Name
- Erstelldatum
- Ersteller (UserId)

## Gruppe
- GruppeId
- EbenenId
- Name

## Fragen
- FragenId
- Titel (Frage)
- Gruppe
- Layer
- Kategorie
- Beschreibung
- ErstellerId

## Audit
- AuditId
- ErstellerId
- Fälligkeitsdatum
- Fragen
- Art (spontan/geplant?)
- Gruppe

## Fragenergebnis
- FragenId
- AuditId
- Farbe
- Kommentar (nur bei Rot)
- Abweichungsgrund (nur bei Rot)
- Bearbeitungsdauer

## Auditergebnis
- UserId
- AuditId
- Dauer
- Startdatum
- Bearbeitungsdauer (Auditzeit)



# Ergänzungen
