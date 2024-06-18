# Exercice : Créer un Composant Standard et un Composant Standalone

### Étape 1 : Créer un Composant Standard

#### Utilisation de Angular CLI

Utilisez Angular CLI pour générer un composant standard appelé `standard-message` :

```bash
ng generate component standard-message
```

#### Définir le Composant Standard

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

#### Déclarer le Composant dans un Module

Ouvrez le fichier `app.module.ts` et ajoutez le composant `StandardMessageComponent` aux déclarations du module.

**app.module.ts**

```typescript
import { NgModule } from "@angular/core";
import { BrowserModule } from "@angular/platform-browser";
import { AppComponent } from "./app.component";
import { StandardMessageComponent } from "./standard-message/standard-message.component";

@NgModule({
  declarations: [AppComponent, StandardMessageComponent],
  imports: [BrowserModule],
  providers: [],
  bootstrap: [AppComponent],
})
export class AppModule {}
```

#### Utiliser le Composant Standard dans le Template Principal

Ouvrez le fichier `app.component.html` et ajoutez le sélecteur du composant `StandardMessageComponent`.

**app.component.html**

```html
<div>
  <app-standard-message></app-standard-message>
</div>
```

### Étape 2 : Créer un Composant Standalone

#### Utilisation de Angular CLI

Utilisez Angular CLI pour générer un composant standalone appelé `standalone-message` :

```bash
ng generate component standalone-message --standalone
```

#### Définir le Composant Standalone

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

#### Utiliser le Composant Standalone dans le Composant Principal

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

#### Ajouter le Sélecteur du Composant Standalone dans le Template Principal

Ouvrez le fichier `app.component.html` et ajoutez le sélecteur du composant `StandaloneMessageComponent`.

**app.component.html**

```html
<div>
  <app-standard-message></app-standard-message>
  <app-standalone-message></app-standalone-message>
</div>
```

### Lancer l'Application

Lancez votre application pour voir les composants en action :

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir les deux composants affichant leurs messages respectifs.

### Explication

- **Composant Standard** : Ce composant est déclaré dans un module (`AppModule`) et utilisé dans le template principal via son sélecteur.
- **Composant Standalone** : Ce composant est autonome et n'a pas besoin d'être déclaré dans un module. Il est directement importé et utilisé dans le composant principal.
