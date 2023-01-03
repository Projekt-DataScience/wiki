# Technologien
Raphi

# Architektur
![Image of Architecture](images/frontend_abstract_architecture.png)


# Ordnerstruktur
Raphi

# Namenskonvention
Raphi

# Assets
In den Assets werden derzeit alle verwendeten Icons und Bilder gespeichert.
Die Icons sind in der entsprechenden Library eingefügt und sind nur für den Wiedergebrauch zusätzlich abgelegt.
Das Login-Bild sollte in Zukunft aus dem Backend kommen und kann auf die nutzende Firma angepasst werden.
<br/><br/>

# Libraries
## Components
### Import von Komponenten
Mit dem folgenden Import können die einzelnen Komponenten aus der übergeordneten Library in den Komponenten und Seiten der Module installiert werden. Im Anschluss werden die Funktionen der einzelnen Komponenten und ihre `Props` und `Emits` näher beschrieben.
```ts
import {AppButtonPrimary, AppButtonSecondary, AppButtonTertiary} from "./libraries/components"
```
<br/><br/>

### Registrieren von Komponenten
Im Folgenden wird beschrieben, wie neue Komponenten in der Library registriert werden können.
<br/><br/>

### Inhaltsverzeichnis
**Button**<br />
Ein Button ist eine Komponente, die eine Call to Action (oder einen Link, aber das sollte vermieden werden) definiert.
- [AppButtonOption](#appbuttonoption)
- [AppButtonPrimary](#appbuttonprimary)
- [AppButtonSecondary](#appbuttonsecondary)
- [AppButtonTertiary](#appbuttontertiary)
<br/><br/>

Spezielle Buttons
- [AppButtonAdd](#appbuttonadd)
- [AppButtonNotification](#appbuttonnotification)
- [AppButtonProfile](#appbuttonprofile)
- [AppButtonThemeToggle](#appbuttonthemetoggle)
<br/><br/>

**Inputs**<br />
Ein Input ist eine Komponente, über die bestimmte Inhalte eingegeben werden können.
- [AppInputTextField](#appinputbigtextfield)
- [AppInputDropdown](#appinputdropdown)
- [AppInputTextField](#appinputtextfield)
<br/><br/>

Container und Listen
- [AppContainer](#appcontainer)
- [AppListContainer](#applistcontainer)
- [AppListText](#applisttext)
- [AppListTextAndSubtext](#applisttextandsubtext)
- [AppListTextWithDividerLines](#applisttextwithdividerlines)
- [AppPageLayout](#apppagelayout)
- [AppTaskList](#apptasklist)
<br/><br/>

Sidebar Komponenten
- [AppNavigationItem](#appnavigationitem)
- [AppNavigationItemActive](#appnavigationitemactive)
- [AppSidebar](#appsidebar)
- [AppSidebarHeader](#appsidebarheader)
- [AppSidebarHeaderSmall](#appsidebarheadersmall)
<br/><br/>

Sonstige Komponenten
- [AppIconLibrary](#appiconlibrary)
- [AppPopup](#apppopup)
- [AppSearchAndFilterBar](#appsearchandfilterbar)
<br/><br/>

### AppButtonAdd
Der AppButtonAdd ist ein spezieller Button, der für das Hinzufügen von neuen Inhalten verwendet wird. Auf der Configuration Page wird er beispielsweise eingesetzt, um neue Geplante Audits zu erstellen.

<br/><br/>
**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | name | Ja | - | Dieser Prop übergibt den Namen, der als Call to Action im Button angezeigt wird. |
| Prop | id | Nein | null | Mit diesem Prop kann für den Button eine ID vergeben werden. |


<br/><br/>

### AppButtonNotification
Der AppButtonNotification ist ein spezieller Button, der einen Popup mit aktuellen Aufgaben öffnet. Er zeigt außerdem als Label an, wie viele offene Aufgaben es aktuell gibt.

<br/><br/>
**Aktionen:**

Die Komponente verfügt über keine Aktionen.

<br/><br/>


### AppButtonOption
Der AppButtonOption ist der Button, der für Einstellungen in Containern und Listen verwendet wird. Über ihn können beispielsweise Elemente gelöscht oder bearbeitet werden. In der ersten Phase der Roadmap haben wir allerdings nur den Button umgesetzt und noch keine Einstellmöglichkeiten hinterlegt.

<br/><br/>
**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | isVertical | Ja | - | Dieser Prop beschreibt, ob der Button horizontal oder vertikal verwendet wird. |
| Emit | buttonClick | - | - | Beim Klicken des Buttons wird ein Event ausgelöst, dass die Eltern der Komponente überwachen können. |
<br/><br/>

### AppButtonPrimary
Der AppButtonPrimary ist der Primary Button des Designsystems und wird für die wichtigsten Call to Actions verwendet. Dadurch kann eine Button Hierarchie auf der Seite oder in der Komponente etabliert werden.

<br/><br/>
**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | isActive | Ja | - | Dieser Prop beschreibt, ob der Button geklickt werden kann oder nicht. |
| Prop | name | Ja | - | Der angezeigte Name des Buttons, der für die Call to Action verwendet wird. |
| Emit | buttonClick | - | - | Beim Klicken des Buttons wird ein Event ausgelöst, dass die Eltern der Komponente überwachen können. |
| Slot | icon | - | - | In diesen Slot kann ein Icon eingefügt werden, dass im Button angezeigt wird. |


<br/><br/>



### AppButtonProfile
Der AppButtonProfile ist ein spezieller Button, der einen Popup mit den wichtigsten Einstellmöglichkeiten für das Profil öffnet.

<br/><br/>
**Aktionen:**

Die Komponente verfügt über keine Aktionen.

<br/><br/>

### AppButtonSecondary
Der AppButtonSecondary wird für die zweitwichtigsten Call to Actions verwendet. Dadurch kann eine Button Hierarchie auf der Seite oder in der Komponente etabliert werden.

<br/><br/>
**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | name | Ja | - | Der angezeigte Name des Buttons, der für die Call to Action verwendet wird. |
| Emits | buttonClick | - | - | Beim Klicken des Buttons wird ein Event ausgelöst, dass die Eltern der Komponente überwachen können. |


<br/><br/>

### AppButtonTertiary
Der AppButtonTertiary wird für die drittwichtigsten Call to Actions verwendet. Dadurch kann eine Button Hierarchie auf der Seite oder in der Komponente etabliert werden.

<br/><br/>
**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | name | Ja | - | Der angezeigte Name des Buttons, der für die Call to Action verwendet wird. |
| Prop | id | Nein | null | Mit diesem Prop kann für den Button eine ID vergeben werden. |
| Prop | isActive | Nein | true | Dieser Prop beschreibt, ob der Button geklickt werden kann oder nicht. |
| Emits | buttonClick | - | - | Beim Klicken des Buttons wird ein Event ausgelöst, dass die Eltern der Komponente überwachen können. |


<br/><br/>

### AppButtonThemeToggle
Der AppButtonThemeToggle ist ein spezieller Button, der für die Einstellung des Themes verwendet wird. Mit ihm lässt sich zwischen Light- und Darkmode umschalten.

<br/><br/>
**Aktionen:**

Die Komponente verfügt über keine Aktionen.
<br/><br/>

### AppContainer
### AppIconLibrary
### AppInputBigTextField
### AppInputDropdown
### AppInputTextField
### AppListContainer
### AppListText
### AppListTextAndSubtext
### AppListTextWithDividerLines
### AppNavigationItem
### AppNavigationItemActive
### AppPageLayout
### AppPopup
### AppSearchAndFilterBar
### AppSidebar
### AppSidebarHeader
### AppSidebarHeaderSmall
### AppTaskList

## Interfaces

## Mixins

## Services

## Stores

# Modules

## LPA
### Components
#### LPADashboard

### Interfaces

### Router

### Stores

### Views

## Main

### Components

### Router

### Stores

### Views

# Router

