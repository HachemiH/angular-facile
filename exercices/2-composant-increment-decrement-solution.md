### Étape 1 : Créer un Nouveau Composant Standalone

Utilisez Angular CLI pour générer un nouveau composant standalone appelé `counter-buttons` :

```bash
ng generate component counter-buttons --standalone
```

### Étape 2 : Ajouter la Logique d'Incrémentation et de Décrémentation

Ouvrez le fichier `counter-buttons.component.ts` et ajoutez la logique pour émettre des événements lorsque les boutons sont cliqués.

#### `counter-buttons.component.ts`

```typescript
import { Component, Output, EventEmitter } from "@angular/core";

@Component({
  selector: "app-counter-buttons",
  template: `
    <button (click)="increment()">Incrémenter</button>
    <button (click)="decrement()">Décrémenter</button>
  `,
  standalone: true,
})
export class CounterButtonsComponent {
  @Output() incrementEvent = new EventEmitter<void>();
  @Output() decrementEvent = new EventEmitter<void>();

  increment() {
    this.incrementEvent.emit();
  }

  decrement() {
    this.decrementEvent.emit();
  }
}
```

### Étape 3 : Émettre des Événements depuis le Composant

Les méthodes `increment` et `decrement` utilisent `this.incrementEvent.emit()` et `this.decrementEvent.emit()` pour émettre les événements `incrementEvent` et `decrementEvent`.

### Étape 4 : Écouter les Événements dans le Composant Parent

Ouvrez le fichier `app.component.ts` et importez le composant `CounterButtonsComponent`. Ajoutez des méthodes pour incrémenter et décrémenter la valeur du compteur.

#### `app.component.ts`

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
  compteur: number = 0;

  incrementerCompteur() {
    this.compteur++;
  }

  decrementerCompteur() {
    this.compteur--;
  }
}
```

### Étape 5 : Afficher la Valeur Incrémentée et Décrémentée

Ouvrez le fichier `app.component.html` et ajoutez le sélecteur du composant `CounterButtonsComponent`. Écoutez les événements `incrementEvent` et `decrementEvent` et appelez les méthodes correspondantes.

#### `app.component.html`

```html
<div>
  <h1>Compteur : {{ compteur }}</h1>
  <app-counter-buttons
    (incrementEvent)="incrementerCompteur()"
    (decrementEvent)="decrementerCompteur()"
  >
  </app-counter-buttons>
</div>
```

### Correction Complète

Voici la solution complète pour l'exercice.

#### `counter-buttons.component.ts`

```typescript
import { Component, Output, EventEmitter } from "@angular/core";

@Component({
  selector: "app-counter-buttons",
  template: `
    <button (click)="increment()">Incrémenter</button>
    <button (click)="decrement()">Décrémenter</button>
  `,
  standalone: true,
})
export class CounterButtonsComponent {
  @Output() incrementEvent = new EventEmitter<void>();
  @Output() decrementEvent = new EventEmitter<void>();

  increment() {
    this.incrementEvent.emit();
  }

  decrement() {
    this.decrementEvent.emit();
  }
}
```

#### `app.component.ts`

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
  compteur: number = 0;

  incrementerCompteur() {
    this.compteur++;
  }

  decrementerCompteur() {
    this.compteur--;
  }
}
```

#### `app.component.html`

```html
<div>
  <h1>Compteur : {{ compteur }}</h1>
  <app-counter-buttons
    (incrementEvent)="incrementerCompteur()"
    (decrementEvent)="decrementerCompteur()"
  >
  </app-counter-buttons>
</div>
```

### Lancer l'Application

Lancez votre application pour voir les composants en action :

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir les boutons d'incrémentation et de décrémentation fonctionnant correctement.

### Explication

- **Composant `CounterButtonsComponent`** : Ce composant émet deux événements, `incrementEvent` et `decrementEvent`, lorsqu'il est cliqué.
- **Composant `AppComponent`** : Ce composant écoute les événements `incrementEvent` et `decrementEvent` et met à jour la valeur du compteur en conséquence.
