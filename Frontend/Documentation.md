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


# Libraries
## Components
Mit dem folgenden Import können die einzelnen Komponenten aus der übergeordneten Library in den Komponenten und Seiten der Module installiert werden. Im Anschluss werden die Funktionen der einzelnen Komponenten und ihre `Props` und `Emits` näher beschrieben.
```ts
import {AppButtonPrimary, AppButtonSecondary, AppButtonTertiary} from "./libraries/components"
```

Auch registrieren von neuen Komponenten in der Library
<br/><br/>

### Inhaltsverzeichnis
Buttons
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

### AppButtonAdd
### AppButtonNotification
### AppButtonOption
### AppButtonPrimary
Der Primary Button wird für die wichtigsten Links und Funktionen verwendet.

| Prop | Pflicht | Standardwert | Beschreibung |
|-----------------|---------------------------------------------|-----------------|-----------------|
| isActive | Ja | - | Dieser Prop beschreibt, ob der Button geklickt werden kann oder nicht. |
| name | Ja | - | Der angezeigte Name des Buttons |

Beim Klicken des Buttons wird ein Event ausgelöst, dass die Eltern überwachen können:
| Emit | Variablen | Beschreibung |
|-----------------|---------------------------------------------|-----------------|
| buttonClick | Ja | - | Dieser Prop beschreibt, ob der Button geklickt werden kann oder nicht. |
```ts
this.$emit('buttonClick')
```

Slots:


### AppButtonProfile
### AppButtonSecondary
### AppButtonTertiary
### AppButtonThemeToggle

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

