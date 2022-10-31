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

#### Mitarbeiter
[...snip...]

#### System
[...snip...]

## Wunschkriterien
Hier werden alle Kriterien beschrieben, die das Produkt können sollte,
um die Wünsche an das zu entwickelnde Produkt so gut wie möglich zu erfüllen.

## Abgrenzungskriterien

Folgende Ziele werden bei dem neuen Produkt bewusst **nicht** verfolgt:

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

## Detailbeschreibung Use-Cases

[...snip...]

**/UC6.1/ Eigene Jahres-Stunden-Übersicht einsehen**

**Übersicht**

  |||
 ---------------|---------------------------------------------------------------
  Ziel          | Einsicht in eigene Jahres-Stunden-Übersicht
  Vorbedingung  | User ist als Mitarbeiter eingeloggt
  Resultat      | User weiß wie viele Stunden er pro Monat im aktuellen Jahr gearbeitet hat
  Nutzer        | Mitarbeiter
  Auslöser      | Übersicht auswählen, unter der Funktion Zeiterfassung
  ------------------------------------------------------------------------------

**Detailbeschreibung**

**Name:** Einsicht in eigene Jahres-Stunden-Übersicht

**Kurzbeschreibung:** Der User hat die Möglichkeit seine eigene Jahres-Stunden-Übersicht zu sehen. Dadurch weiß er wieviel er pro Monat gearbeitet hat, wieviel er arbeiten hätte sollen und was sein Stundensaldo in dem Monat war. Für jeden Monat wird eine Box dargestellt mit diesen Daten.

**Akteure:**
* Mitarbeiter
* Zeiterfassungsdatenbank

**Auslöser:** Mitarbeiter führt das Mitarbeiterzeiterfassungsprogramm aus und geht auf Zeiterfassung

**Ergebnisse:** Jahres-Stunden-Übersicht im angegebenen Jahr wird angezeigt

**Eingehende Daten:**
* Session ID
* Mitarbeiter ID
* Auswahl, dass der User Jahres-Stunden-Übersicht ansehen möchte
* Das ausgewählte Jahr (kann auch ein Standardwert existieren, sodass das Jahr nicht vom User explizit angegeben werden muss)

**Vorbedingung:** User ist als Mitarbeiter eingeloggt

**Nachbedingung** User ist immernoch als Mitarbeiter eingeloggt; Anzeigen der Ansicht für die Jahres-Stunden-Übersicht

**Essenzielle Schritte:**
  1. Use Case Login
  2. User klickt auf Zeiterfassung
  3. User klickt auf Übersicht
  4. Zeiterfassungsdatenbank gibt Jahres-Stunden-Übersicht des Mitarbeiters zurück
  5. Jahres Stunden Übersicht wird angezeigt

**Ausnahmen**
* zu 4: Falls noch keine Jahres-Stunden-Übersicht existiert:
  - 4a) Anzeigen, dass keine Jahres-Stunden-Übersicht existiert

* zu 4: Datenbankfehler jeglicher Art
  - 4b) Operationen abbrechen
  - 4c) User anzeigen, dass es einen Fehler gab und dass er es noch einmal versuchen soll. Falls dieser Fehler besteht soll er einen Administrator kontaktieren
  - 4d) Bei 2. fortsetzen

**Änderungshistorie:** 
* 01.04.2020; Korkmatik; Anwendungsfall angelegt

[...snip...]

## Offene Punkte

&lt; *Hier werden alle offenen Fragen gesammelt. In der Final-Version
darf hier nichts mehr stehen!* &gt;

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

# Ergänzungen
