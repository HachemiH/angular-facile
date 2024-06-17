# Exercice 1 : Créer un Bouton d'Incrémentation Autonome

## Étape 1 : Créer un Nouveau Composant Standalone

Utilisez Angular CLI pour générer un nouveau composant standalone appelé `increment-button` :

```bash
ng generate component increment-button --standalone
```

## Étape 2 : Ajouter la Logique d'Incrémentation

Ouvrez le fichier `increment-button.component.ts` et ajoutez la logique pour gérer l'état du compteur et incrémenter la valeur.

### `increment-button.component.ts`

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-increment-button",
  templateUrl: "./increment-button.component.html",
  styleUrls: ["./increment-button.component.css"],
  standalone: true,
})
export class IncrementButtonComponent {
  compteur: number = 0;

  increment() {
    this.compteur++;
  }
}
```

## Étape 3 : Ajouter le Template HTML

Ouvrez le fichier `increment-button.component.html` et ajoutez le template HTML pour afficher la valeur du compteur et le bouton d'incrémentation.

### `increment-button.component.html`

```html
<div>
  <p>Compteur : {{ compteur }}</p>
  <button (click)="increment()">Incrémenter</button>
</div>
```

## Étape 4 : Utiliser le Composant dans le Composant Parent

Ouvrez le fichier `app.component.ts` et importez le composant `IncrementButtonComponent`.

### `app.component.ts`

```typescript
import { Component } from "@angular/core";
import { RouterOutlet } from "@angular/router";
import { IncrementButtonComponent } from "./increment-button/increment-button.component";

@Component({
  selector: "app-root",
  standalone: true,
  imports: [RouterOutlet, IncrementButtonComponent],
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"],
})
export class AppComponent {
  title = "atelier-angular";
}
```

## Étape 5 : Ajouter le Sélecteur du Composant dans le Template Principal

Ouvrez le fichier `app.component.html` et ajoutez le sélecteur du composant `IncrementButtonComponent`.

### `app.component.html`

```html
<div>
  <app-increment-button></app-increment-button>
</div>
```

## Lancer l'Application

Lancez votre application pour voir le composant en action :

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir le bouton d'incrémentation fonctionnant correctement et affichant la valeur du compteur.

## Explication

- **Composant `IncrementButtonComponent`** : Ce composant est autonome et gère lui-même l'état du compteur. Il affiche la valeur du compteur et incrémente cette valeur lorsqu'il est cliqué.
- **Composant `AppComponent`** : Ce composant utilise simplement le composant `IncrementButtonComponent` sans avoir à gérer l'état du compteur.
