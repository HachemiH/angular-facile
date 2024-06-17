# Exercice 2 : Créer un Composant avec Incrémentation et Décrémentation

## Étape 1 : Créer un Nouveau Composant Standalone

Utilisez Angular CLI pour générer un nouveau composant standalone appelé `counter-buttons` :

```bash
ng generate component counter-buttons --standalone
```

## Étape 2 : Ajouter la Logique d'Incrémentation et de Décrémentation

Ouvrez le fichier `counter-buttons.component.ts` et ajoutez la logique pour gérer l'état du compteur, l'incrémentation et la décrémentation.

### `counter-buttons.component.ts`

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-counter-buttons",
  templateUrl: "./counter-buttons.component.html",
  styleUrls: ["./counter-buttons.component.css"],
  standalone: true,
})
export class CounterButtonsComponent {
  compteur: number = 0;

  increment() {
    this.compteur++;
  }

  decrement() {
    this.compteur--;
  }
}
```

## Étape 3 : Ajouter le Template HTML

Ouvrez le fichier `counter-buttons.component.html` et ajoutez le template HTML pour afficher la valeur du compteur et les boutons d'incrémentation et de décrémentation.

### `counter-buttons.component.html`

```html
<div>
  <p>Compteur : {{ compteur }}</p>
  <button (click)="increment()">Incrémenter</button>
  <button (click)="decrement()">Décrémenter</button>
</div>
```

## Étape 4 : Utiliser le Composant dans le Composant Parent

Ouvrez le fichier `app.component.ts` et importez le composant `CounterButtonsComponent`.

### `app.component.ts`

```typescript
import { Component } from "@angular/core";
import { RouterOutlet } from "@angular/router";
import { CounterButtonsComponent } from "./counter-buttons/counter-buttons.component";

@Component({
  selector: "app-root",
  standalone: true,
  imports: [RouterOutlet, CounterButtonsComponent],
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"],
})
export class AppComponent {
  title = "atelier-angular";
}
```

## Étape 5 : Ajouter le Sélecteur du Composant dans le Template Principal

Ouvrez le fichier `app.component.html` et ajoutez le sélecteur du composant `CounterButtonsComponent`.

### `app.component.html`

```html
<div>
  <app-counter-buttons></app-counter-buttons>
</div>
```

## Lancer l'Application

Lancez votre application pour voir le composant en action :

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir les boutons d'incrémentation et de décrémentation fonctionnant correctement et affichant la valeur du compteur.

## Explication

- **Composant `CounterButtonsComponent`** : Ce composant est autonome et gère lui-même l'état du compteur. Il affiche la valeur du compteur et permet à l'utilisateur de l'incrémenter ou de la décrémenter en cliquant sur les boutons.
- **Composant `AppComponent`** : Ce composant utilise simplement le composant `CounterButtonsComponent` sans avoir à gérer l'état du compteur.
