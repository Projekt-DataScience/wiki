## Installation der Entwicklungsumgebung

Auf dieser Seite wird das Klonen und Einrichten der Entwicklungsumgebung für das Frontend in Visual Studio Code beschrieben.

- [Lokale Einrichtung](#lokale-einrichtung)
- [Initiale Konfiguration](#initiale-konfiguration)
<br/><br/>

## Lokale Einrichtung
In diesem Absatz wird das Klonen und Einrichten der Entwicklungsumgebung für das Frontend beschrieben.
<br/><br/>

#### Vorbereitung
Zuerst muss global [Git](https://git-scm.com/downloads) und [NodeJS](https://nodejs.org/en/download/) installiert werden. Dabei wird empfohlen, für die NodeJS Installation [NVM](https://github.com/nvm-sh/nvm) zu verwenden. Mit diesem Versionsmanager können mehrere NodeJS Versionen installiert und verwaltet werden. Wir benötigen für das Frontend die Version 16 LTS (16.0.0). Im weiteren Verlauf wird NVM vorausgesetzt. Als Code Editor empfehlen wir die Installation von Visual Studio Code. Nach den Installationen muss der PC neu gestartet werden. 

```bash
npm install -g yarn
yarn --version
```
<br/><br/>

Falls Windows 10 die Ausführung des PowerShell-Skripts verweigert, muss die PowerShell als Administrator ausgeführt und der folgende Befehl eingegeben werden.
```bash
Set-ExecutionPolicy RemoteSigned
```
<br/><br/>

#### Klonen des Github Repos
Mit dem folgenden Befehl kann im passenden Ordner das Repository geklont werden.
```bash
git clone https://github.com/Projekt-DataScience/frontend.git
```
<br/><br/>

#### Wechseln in den Projektordner
Als nächstes muss in den Projektordner gewechselt werden.
```bash
cd frontend
```
<br/><br/>

#### Installation von NPM
Als nächstes wird die aktuelle NodeJS Version mit NVM festgelegt. Mit ls werden die aktuell installierten Versionen angezeigt und mit use kann man die benötigte Version für den Ordner festlegen.
```bash
nvm ls
nvm use 16.0.0
```
<br/><br/>

Anschließend können die nötigen Dependencies für das Frontend installiert werden.
```bash
npm install
```
<br/><br/>

#### Starten der Anwendung
Der folgende Befehl startet den Entwicklungsserver und damit die Anwendung. Hinweis: Für den Betrieb des Frontends muss selbstverständlich auch das Backend eingerichtet sein, um sich einzuloggen und die benötigten Daten anzuzeigen.
```bash
npm run dev
```
<br/><br/>

## Initiale Konfiguration
In diesem Absatz wird die verwendete Konfiguration für das einmalige Aufsetzen der Entwicklungsumgebung beschrieben (die oben beschriebene [Anleitung](#lokale-einrichtung) ist zum Entwickeln und Starten der Anwendung ausreichend).
<br/><br/>

#### Vorbereitung
Als Vorbereitung musste global `Vite` installiert werden.
```bash
npm i -g vite
```
<br/><br/>

#### Erstellen der Vuejs Installation
Mit dem folgenden Befehl kann ein neues Vuejs Projekt erstellt werden.
```bash
npm create tw <project name>
```

Konfiguration von Vite

![Konfiguration Vite](images/vite-konfiguration.png)
<br/><br/>

#### Installation von Prettier
Mit dem folgenden Befehl wurde Prettier installiert.
```bash
yarn add --dev prettier
```
<br/><br/>

#### Installation von Vue Router und Vuex
Für die Seitennavigation musste Vue Router installiert werden.
```bash
yarn add vue-router@4
yarn add pinia
```
<br/><br/>

#### Konfiguration von Vue Router und Vuex
Anschließend müssen einige Projektdateien angepasst werden, damit Vue Router und Vuex funktionieren. Als erstes wird die `main.ts` abgeändert.
```javascript
/* src/main.ts */

import {createApp} from 'vue'
import './style.css'
import App from './App.vue'
import router from './router/index'
import { createPinia } from "pinia";

createApp(App)
  .use(createPinia())
  .use(router)
  .mount('#app')
```
<br/><br/>

Dann wird die `App.vue` angepasst.
```javascript
/* src/App.vue */

<template>
  <div id="app">
    <router-view />
  </div>
</template>
```
<br/><br/>

Als nächstes wird der Ordner `views` und `components` erstellt (sofern nicht vorhanden). Außerdem wird in views die Datei `Home.vue` zum testen angelegt.
```javascript
/* src/views/Home.vue */

<template>
    <h1>Home!!</h1>
</template>
```
<br/><br/>

Nun wird der Ordner `router` erstellt zusammen mit der Datei `index.ts`.
```javascript
/* src/router/index.ts */

import { createRouter, createWebHistory } from 'vue-router'
import Home from '/src/views/Home.vue'
const routes = [
    {
        path: '/',
        name: 'Home',
        component: Home,
    },
]
const router = createRouter({
    history: createWebHistory(),
    routes,
})
export default router
```
<br/><br/>

Anschließend wird der Ordner `store` erstellt zusammen mit der Datei `index.ts` und `types.ts`
```javascript
/* src/store/index.ts */

import { defineStore } from "pinia";
import { ToDoItem } from "./types";

export const useTodoStore = defineStore('ToDoStore', {
  state: () => ({
    todos:[] as ToDoItem[]
  }),
  actions: {
    addTodo(item: string) {
      this.todos.push({ item, id: 1, done: false })
    }
  }
})
```
```javascript
/* src/store/types.ts */

export interface ToDoItem {
    item: string;
    id: number;
    done: boolean;
}
```
