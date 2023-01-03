# Inhaltsverzeichnis
Hier Inhalt

# Technologien
Raphi hier auch ressourcen? oder extern?

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
@Jonas
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

**Container und Listen**<br />
Diese Komponenten werden verwendet, um die Kacheln und Listen des Designsystems zu vereinheitlichen.
- [AppContainer](#appcontainer)
- [AppListContainer](#applistcontainer)
- [AppListText](#applisttext)
- [AppListTextAndSubtext](#applisttextandsubtext)
- [AppListTextWithDividerLines](#applisttextwithdividerlines)
- [AppPageLayout](#apppagelayout)
- [AppTaskList](#apptasklist)
<br/><br/>

**Sidebar**<br />
Die Sidebar wird durch die folgenden Komponenten aufgebaut.
- [AppNavigationItem](#appnavigationitem)
- [AppNavigationItemActive](#appnavigationitemactive)
- [AppSidebar](#appsidebar)
- [AppSidebarHeader](#appsidebarheader)
- [AppSidebarHeaderSmall](#appsidebarheadersmall)
<br/><br/>

**Sonstige**<br />
Die letzten Komponenten des Designsystems, die sich keiner Kategorie eindeutig zuordnen lassen.
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
| Emits | buttonClick | - | - | Beim Klicken des Buttons wird ein Event ausgelöst, dass die Eltern der Komponente überwachen können. Zusätzlich wird auch als Parameter die aktuelle ID des geklickten Buttons übermittelt. |

<br/><br/>

### AppButtonThemeToggle
Der AppButtonThemeToggle ist ein spezieller Button, der für die Einstellung des Themes verwendet wird. Mit ihm lässt sich zwischen Light- und Darkmode umschalten.

<br/><br/>
**Aktionen:**

Die Komponente verfügt über keine Aktionen.
<br/><br/>

### AppContainer
Der AppContainer ist die standardmäßige Kachel des Designsystems. Sie wird beispielsweise auf der LPA Startseite verwendet für die Offenen Audits. Sie benötigt immer den Content-Slot und optional einen Header und Footer Slot. Wenn kein Header-Slot angegeben wird, wird der ContainerName Prop angezeigt.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | containerName | Ja | - | Der angezeigte Name des Containers, der angezeigt wird, wenn kein Header Slot übergeben wird. |
| Slot | header | - | - | Der Header Slot kann optional statt dem containerName als Header des Containers angezeigt werden. So kann beispielsweise neben dem Titel auch ein Button angezeigt werden. |
| Slot | content | Ja | - | Der Inhalt des Containers. |
| Slot | footer | - | - | Der Footer des Containers. Kann beispielsweise für eine Pagination verwendet werden. |

<br/><br/>

### AppIconLibrary
Die aktuelle IconLibrary wird über die Komponente AppIconLibrary realisiert. Durch sie kann sowohl das Styling der Icons angepasst werden als auch Icons dynamisch anhand des icon Props gerendert werden. Ein Beispiel hierfür ist die Main-Dashboard Seite. Hier werden die Applikationen anhand der Informationen aus dem Store dynamisch gerendert.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | icon | Ja | - | Über diesen Prop wird bestimmt, welches Icon angezeigt wird. Ein Beispiel ist der Name "lpa", der das LPA Logo rendert. |
| Prop | styling | Nein | - | Mithilfe dieses Props können TailwindCSS Klassen übergeben werden, die das Aussehen des Buttons festlegen. Beispielsweise die Farbe, Ausrichtung und Größe. |
| Prop | type | Nein | - | Der Type wird nur für manche Icons verwendet und legt fest, wie die Icons aussehen. Beispielsweise kann so die Checkbox entweder "active" oder "inactive" gerendert werden. |

<br/><br/>

**Übersicht über die Icons:**<br/>
Alle Icons mit ihrem Namen und möglichen Type Props. @Jonas
<br/><br/>


**Neues Icon hinzufügen:**<br/>
Als erstes wird ein neuer `div`-Tags eingefügt, der den Namen des Icons als if-Abfrage beinhaltet.

```html
<div v-if="icon === 'history'">
    <!--Insert SVG-->
</div>
```
<br/><br/>

Dann wird der SVG Code des Icons kopiert und in den `div`-Tags eingefügt.

```html
<div v-if="icon === 'history'">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="30.595"
      height="27.034"
      viewBox="0 0 30.595 27.034"
    >
      <g id="LPAHistoryArrowIcon" transform="translate(0.374)">
        <path
          id="Pfad_311"
          data-name="Pfad 311"
          d="M4.188,13.517a12.512,12.512,0,1,1,1.835,6.528"
          fill="none" stroke="#7b808a" stroke-width="2"
          stroke-linecap="round"
          stroke-miterlimit="10"
        />
        <path
          id="Pfad_312"
          data-name="Pfad 312"
          d="M1,8.258l3.188,5.259L9.653,10.01"
          fill="none" stroke="#7b808a" stroke-width="2"
          stroke-linecap="round"
          stroke-miterlimit="10"
        />
        <path
          id="Pfad_313"
          data-name="Pfad 313"
          d="M16.67,5.91v7.607l4.622,4.622"
          fill="none" stroke="#7b808a" stroke-width="2"
          stroke-linecap="round"
          stroke-miterlimit="10"
        />
      </g>
    </svg>
  </div>
```
<br/><br/>

Anschließend werden die Klassen des SVG-Icons an die TailwindCSS Klassen angepasst und der Styling Prop hinzugefügt.

```html
<div v-if="icon === 'history'">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="30.595"
      height="27.034"
      viewBox="0 0 30.595 27.034"
      :class="styling"
    >
      <g id="LPAHistoryArrowIcon" transform="translate(0.374)">
        <path
          id="Pfad_311"
          data-name="Pfad 311"
          d="M4.188,13.517a12.512,12.512,0,1,1,1.835,6.528"
          class="fill-none stroke-current stroke-2"
          stroke-linecap="round"
          stroke-miterlimit="10"
        />
        <path
          id="Pfad_312"
          data-name="Pfad 312"
          d="M1,8.258l3.188,5.259L9.653,10.01"
          class="fill-none stroke-current stroke-2"
          stroke-linecap="round"
          stroke-miterlimit="10"
        />
        <path
          id="Pfad_313"
          data-name="Pfad 313"
          d="M16.67,5.91v7.607l4.622,4.622"
          class="fill-none stroke-current stroke-2"
          stroke-linecap="round"
          stroke-miterlimit="10"
        />
      </g>
    </svg>
  </div>
```
<br/><br/>


### AppInputBigTextField
Die AppInputBigTextField-Komponente wird verwendet, wenn ein langer Text in das Input Feld eingegeben werden soll. Ein Beispiel ist der Kommentar beim Durchführen eines Audits.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | headline | Ja | - | Die Headline wird über dem Input Feld angezeigt und beschreibt den Inhalt, der eingegeben werden soll. |
| Prop | name | Ja | - | Mit diesem Prop kann der Name der Textarea definiert werden. |
| Prop | text | Ja | - | Diese Prop übergibt den aktuellen Inhalt des Textes aus der Elternkomponente oder -seite. |
| Emit | input | - | - | Beim Klicken des Buttons wird ein Event ausgelöst, dass die Eltern der Komponente überwachen können. Zusätzlich wird auch als Parameter der aktuelle Inhalt des Textfeldes übergeben. |

<br/><br/>


### AppInputDropdown
Die AppInputDropdown-Komponente wird verwendet, wenn ein Dropdown-Item im Input Feld ausgewählt werden soll. Ein Beispiel ist der Kommentar beim Durchführen eines Audits.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | headline | Nein | - | Die Headline wird über dem Input Feld angezeigt und beschreibt den Inhalt, der ausgewählt werden soll. |
| Prop | name | Ja | - | Mit diesem Prop kann der Name des Dropdowns definiert werden. |
| Prop | options | Ja | - | Diese Prop übergibt das Array mit den Inhalten, die im Dropdown zur Auswahl stehen. |
| Prop | initialOption | Nein | - | Dieser Prop kann verwendet werden, um den initialen Inhalt des DropDowns festzulegen. Diese Option wird angezeigt, wenn noch kein Inhalt ausgewählt wurde. Beispielsweise kann als String `"-- Grund auswählen --"` übergeben werden. |
| Prop | currentValue | Ja | - | Diese Prop beinhaltet als String die ID des Array-Items, dass aktuell ausgewählt wurde. Wenn noch kein Wert ausgewählt wurde, muss `"null"` als String übergeben werden.  |
| Emit | input | - | - | Beim Klicken des Buttons wird ein Event ausgelöst, dass die Eltern der Komponente überwachen können. Zusätzlich wird auch als Parameter die ID des aktuell ausgewählten Inhalts des Dropdowns übergeben. |

<br/><br/>

### AppInputTextField
@Jonas

<br/><br/>

### AppListContainer
Der AppListContainer wird für Listen verwendet und besitzt drei Spalten. Die linke und rechte Spalte sind optional, die mittlere muss übergeben werden als Slot. Die Komponente ist die Zeile einer Liste. Beispielsweise wird auf der Main Dashboard Seite für jede Zeile das App Icon in den linken Slot, den Namen in den mittleren Slot und ein Button in den rechten Slot der Listenzeile gerendert.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | isLast | Nein | true | Hier wird festgelegt, ob ein neuer Trennstrich gerendert wird oder nicht. Wenn `true` übergeben wird, wird kein Trennstrich angefügt. |
| Prop | alignment | Nein | center | Dieser Prop regelt die vertikale Zentrierung der Zeile. Wird hier beispielsweise `"start"` übergeben, sind alle Elemente nicht zentriert, sondern oben bündig. |
| Slot | wrapperLeft | Nein | - | Dieser Slot rendert die linke Spalte des Containers. |
| Slot | wrapperContent | Ja | - | Dieser Slot rendert die mittlere Spalte des Containers. |
| Slot | wrapperRight | Nein | - | Dieser Slot rendert die rechte Spalte des Containers. |

<br/><br/>

### AppListText
Diese Komponente ist der Text, der in den Containern und Listen verwendet wird. Sie kann auch Teil von anderen Listen Komponenten sein.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | text | Ja | - | Hier wird der Text übergeben, der gerendert werden soll. |

<br/><br/>

### AppListTextAndSubtext
Die AppListTextAndSubtext kombiniert die Komponenten AppListText und AppListTextWithDividerLines. Sie wird standardmäßig für die meisten Listen verwendet und beinhaltet neben dem Haupttitel auch noch einige Parameter als Untertitel.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | text | Ja | - | Hier wird der Text übergeben, der gerendert werden soll. |
| Prop | subtext | Ja | - | In diesem Prop wird als Array der Subtext übergeben, der an die AppListTextWithDividerLines Komponente übergeben werden soll. |

<br/><br/>

### AppListTextWithDividerLines
Die AppListTextWithDividerLines trennt verschiedene Inhalte mit einer blauen Trennlinie. Sie wird beispielsweise für Untertitel in den Listen verwendet. Es können aktuell Bilder-Urls, zweistufige Texte, graue Texte und schwarze Texte übergeben werden.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | text | Nein | - | Hier wird der Text übergeben, der gerendert werden soll. |
| Prop | isLast | Ja | - | Hier wird festgelegt, ob ein neuer Trennstrich gerendert wird oder nicht. Wenn `true` übergeben wird, wird kein Trennstrich angefügt.  |
| Prop | imgPath | Nein | - | Falls angegeben, wird der übergebene String als Bild-Url verwendet. |
| Prop | subtext | Nein | - | Falls angegeben, wird dieser Wert über den aktuellen Text gerendert. Beispielsweise kann so beschrieben werden, was der aktuelle Text bedeutet. Beispielsweise `Auditor` als Subtext und `Tony Stark` als Text. |
| Prop | boldText | Nein | - | Wenn hier `true` übergeben wird, wird der Text nicht grau, sondern schwarz gerendert. |

<br/><br/>

### AppNavigationItem
Die Komponente AppNavigationItem ist das inaktive Pendant zur Komponente AppNavigationItemActive. Beide Komponenten werden als Navigationsitems verwendet. Falls die aktuelle Seite nicht der Seite entspricht, die durch die Komponente beschrieben wird, wird die AppNavigationItem verwendet und nicht die AppNavigationItemActive. In Zukunft könnten die beiden auch in eine Komponenten mit einem isActive Prop überführt werden.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | itemName | Ja | - | Dieser Prop beschreibt den aktuellen Namen des Navigationselements. |
| Prop | routerName | Ja | - | Dieser Prop bestimmt die Seite, zu der über das Navigationselement weitergeleitet wird. |
| Prop | iconName | Ja | - | Dieser Prop beinhaltet das Icon, dass neben dem Namen gerendert wird. |
| Prop | toggleIsActive | Ja | true | Hier wird als Prop von der Elternkomponente übergeben, ob der Sidebar Toggle Button aktuell aktiv ist oder nicht. Ist er nicht aktiv, wird nur das Icon und nicht der Name gerendert. |

<br/><br/>

### AppNavigationItemActive
Die Komponente AppNavigationItemActive ist das aktive Pendant zur Komponente AppNavigationItem. Beide Komponenten werden als Navigationsitems verwendet. Falls die aktuelle Seite nicht der Seite entspricht, die durch die Komponente beschrieben wird, wird die AppNavigationItem verwendet und nicht die AppNavigationItemActive. In Zukunft könnten die beiden auch in eine Komponenten mit einem isActive Prop überführt werden.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | itemName | Ja | - | Dieser Prop beschreibt den aktuellen Namen des Navigationselements. |
| Prop | iconName | Ja | - | Dieser Prop beinhaltet das Icon, dass neben dem Namen gerendert wird. |
| Prop | toggleIsActive | Ja | true | Hier wird als Prop von der Elternkomponente übergeben, ob der Sidebar Toggle Button aktuell aktiv ist oder nicht. Ist er nicht aktiv, wird nur das Icon und nicht der Name gerendert. |

<br/><br/>

### AppPageLayout
Diese Komponente wird auf jeder Seite verwendet und definiert das Layout der Seite. Sie verfügt über einen Header, eine Sidebar, eine Subsidebar und den Content Bereich, auf dem der Inhalt der Seite angezeigt wird. Sie regelt auch den Toggle zwischen der großen und kleinen Sidebar und kümmert sich auch um den Abstand der einzelnen Bereiche untereinander.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Slot | sidebar | Nein | - | Dieser Slot rendert die aktuelle Sidebar der Seite. |
| Slot | subsidebar | Nein | - | Dieser Slot rendert Einstellmöglichkeiten zur aktuellen Seite. Hier könnten zum Beispiel Filteroptionen angezeigt werden. |
| Slot | header | Ja | - | Der Header Slot rendert den aktuellen Header der Seite. |
| Slot | content | Ja | - | Der Content Slot rendert den Content der Seite. |

<br/><br/>

### AppPopup
Diese Komponente rendert den Popup auf den verschiedenen Seiten.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Slot | - | Ja | - | Dieser Slot rendert den Inhalt des Popups. |

<br/><br/>

### AppSearchAndFilterBar
Die AppSearchAndFilterBar ist die typische Header Komponente für die verschiedenen Seiten. Aktuell funktioniert die Suche nicht, sie soll aber in Zukunft als Filter für die Seite fungieren.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Slot | wrapperRight | Nein | - | Dieser Slot rendert die rechte Seite des Headers. Beispielsweise kann hier ein Button mit einer Call to Action eingefügt werden. |

<br/><br/>

### AppSidebar
Diese Komponente ist die übergeordnete Sidebar für alle Module. Sie besitzt einen Slot für den Header und einen Slot für die Navigation Items. Zusätzlich zeigt sie auch den DualSidebarButton an, der sowohl Einstellmöglichkeiten als auch aktuelle Aufgaben beinhaltet.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | toggleIsActive | Ja | true | Hier wird als Prop von der Elternkomponente übergeben, ob der Sidebar Toggle Button aktuell aktiv ist oder nicht. Ist er nicht aktiv, wird nur das Icon und nicht der Name gerendert. |
| Slot | navigationItems | Ja | - | Dieser Slot rendert die Navigation Items des Moduls. |
| Slot | sidebarHeader | Ja | - | Dieser Slot rendert den Header des Moduls. |

<br/><br/>

### AppSidebarHeader
Der AppSidebarHeader ist der aktuelle Header des Moduls.

<br/><br/>

**Aktionen:**

| Typ | Name | Pflicht | Standardwert | Beschreibung |
|-----------------|-----------------|---------------------------------------------|-----------------|-----------------|
| Prop | brandingName | Ja | - | Dieser Prop übergibt den Markennamen an den Header. Beispielsweise `"MyCompany"`. |
| Prop | moduleName | Ja | - | Dieser Prop übergibt den Namen des Moduls an den Header. Beispielsweise `"Layered Process Audit"`. |
| Emit | toggleIsActive | - | - | Beim Klicken des Sidebar Toggle Buttons wird ein Event ausgelöst, dass die Eltern der Komponente überwachen können. |
| Slot | - | Ja | - | Dieser Slot übergibt das Icon des Headers an die Komponente. |

<br/><br/>

### AppSidebarHeaderSmall
Diese Komponente wurde begonnen, aber noch nicht fertig gestellt (da wir uns für den AppSidebarHeader entschieden haben).

<br/><br/>

### AppTaskList
@Jonas

<br/><br/>

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

