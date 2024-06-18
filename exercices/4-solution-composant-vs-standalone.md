# Exercice : Créer un Composant Standard et un Composant Standalone

## Objectif

1. Créer un composant standard (non standalone) pour afficher un message.
2. Créer un composant standalone pour afficher un autre message.

## Étape 1 : Créer un Composant Standard

## Utilisation de Angular CLI

Utilisez Angular CLI pour générer un composant standard appelé `standard-message` :

```bash
ng generate component standard-message
```

### Définir le Composant Standard

**standard-message.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-standard-message",
  templateUrl: "./standard-message.component.html",
  styleUrls: ["./standard-message.component.css"],
})
export class StandardMessageComponent {
  message: string = "Ceci est un composant standard";
}
```

**standard-message.component.html**

```html
<p>{{ message }}</p>
```

### Déclarer le Composant dans la Configuration de l'Application

Ouvrez le fichier `app.config.ts` et ajoutez le composant `StandardMessageComponent` aux déclarations de la configuration.

**app.config.ts**

```typescript
import { ApplicationConfig } from "@angular/core";
import { provideRouter } from "@angular/router";
import { importProvidersFrom } from "@angular/core";
import { BrowserModule } from "@angular/platform-browser";
import { StandardMessageComponent } from "./standard-message/standard-message.component";

export const appConfig: ApplicationConfig = {
  providers: [
    provideRouter([]),
    importProvidersFrom(BrowserModule),
    StandardMessageComponent,
  ],
};
```

### Utiliser le Composant Standard dans le Template Principal

Ouvrez le fichier `app.component.html` et ajoutez le sélecteur du composant `StandardMessageComponent`.

**app.component.html**

```html
<div>
  <app-standard-message></app-standard-message>
</div>
```

## Étape 2 : Créer un Composant Standalone

### Utilisation de Angular CLI

Utilisez Angular CLI pour générer un composant standalone appelé `standalone-message` :

```bash
ng generate component standalone-message --standalone
```

### Définir le Composant Standalone

**standalone-message.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-standalone-message",
  templateUrl: "./standalone-message.component.html",
  styleUrls: ["./standalone-message.component.css"],
  standalone: true,
})
export class StandaloneMessageComponent {
  message: string = "Ceci est un composant standalone";
}
```

**standalone-message.component.html**

```html
<p>{{ message }}</p>
```

### Utiliser le Composant Standalone dans le Composant Principal

Ouvrez le fichier `app.component.ts` et importez le composant `StandaloneMessageComponent`.

**app.component.ts**

```typescript
import { Component } from "@angular/core";
import { StandaloneMessageComponent } from "./standalone-message/standalone-message.component";

@Component({
  selector: "app-root",
  standalone: true,
  imports: [StandaloneMessageComponent],
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"],
})
export class AppComponent {
  title = "atelier-angular";
}
```

### Ajouter le Sélecteur du Composant Standalone dans le Template Principal

Ouvrez le fichier `app.component.html` et ajoutez le sélecteur du composant `StandaloneMessageComponent`.

**app.component.html**

```html
<div>
  <app-standard-message></app-standard-message>
  <app-standalone-message></app-standalone-message>
</div>
```

## Lancer l'Application

Lancez votre application pour voir les composants en action :

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir les deux composants affichant leurs messages respectifs.

## Explication

- **Composant Standard** : Ce composant est déclaré dans la configuration de l'application (`app.config.ts`) et utilisé dans le template principal via son sélecteur.
- **Composant Standalone** : Ce composant est autonome et n'a pas besoin d'être déclaré dans un module. Il est directement importé et utilisé dans le composant principal.
