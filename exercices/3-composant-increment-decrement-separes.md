# Exercice 3 : Séparer les Composants Incrément et Décrément

### Étape 1 : Créer les Composants Standalone

#### Créer le Composant Incrément

Utilisez Angular CLI pour générer le composant standalone pour l'incrémentation :

```bash
ng generate component increment-button --standalone
```

#### Créer le Composant Décrément

Utilisez Angular CLI pour générer le composant standalone pour la décrémentation :

```bash
ng generate component decrement-button --standalone
```

### Étape 2 : Ajouter la Logique d'Incrémentation et de Décrémentation

#### `increment-button.component.ts`

Ouvrez le fichier `increment-button.component.ts` et ajoutez la logique pour émettre un événement lorsque le bouton est cliqué.

```typescript
import { Component, Output, EventEmitter } from "@angular/core";

@Component({
  selector: "app-increment-button",
  templateUrl: "./increment-button.component.html",
  styleUrls: ["./increment-button.component.css"],
  standalone: true,
})
export class IncrementButtonComponent {
  @Output() incrementEvent = new EventEmitter<void>();

  increment() {
    this.incrementEvent.emit();
  }
}
```

#### `increment-button.component.html`

Ouvrez le fichier `increment-button.component.html` et ajoutez le template HTML pour le bouton d'incrémentation.

```html
<button (click)="increment()">Incrémenter</button>
```

#### `decrement-button.component.ts`

Ouvrez le fichier `decrement-button.component.ts` et ajoutez la logique pour émettre un événement lorsque le bouton est cliqué.

```typescript
import { Component, Output, EventEmitter } from "@angular/core";

@Component({
  selector: "app-decrement-button",
  templateUrl: "./decrement-button.component.html",
  styleUrls: ["./decrement-button.component.css"],
  standalone: true,
})
export class DecrementButtonComponent {
  @Output() decrementEvent = new EventEmitter<void>();

  decrement() {
    this.decrementEvent.emit();
  }
}
```

#### `decrement-button.component.html`

Ouvrez le fichier `decrement-button.component.html` et ajoutez le template HTML pour le bouton de décrémentation.

```html
<button (click)="decrement()">Décrémenter</button>
```

### Étape 3 : Émettre des Événements depuis les Composants

Les méthodes `increment` et `decrement` utilisent `this.incrementEvent.emit()` et `this.decrementEvent.emit()` pour émettre les événements `incrementEvent` et `decrementEvent`.

### Étape 4 : Écouter les Événements dans le Composant Parent

Ouvrez le fichier `app.component.ts` et importez les composants `IncrementButtonComponent` et `DecrementButtonComponent`. Ajoutez des méthodes pour incrémenter et décrémenter la valeur du compteur.

#### `app.component.ts`

```typescript
import { Component } from "@angular/core";
import { RouterOutlet } from "@angular/router";
import { IncrementButtonComponent } from "./increment-button/increment-button.component";
import { DecrementButtonComponent } from "./decrement-button/decrement-button.component";

@Component({
  selector: "app-root",
  standalone: true,
  imports: [RouterOutlet, IncrementButtonComponent, DecrementButtonComponent],
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

Ouvrez le fichier `app.component.html` et ajoutez les sélecteurs des composants `IncrementButtonComponent` et `DecrementButtonComponent`. Écoutez les événements `incrementEvent` et `decrementEvent` et appelez les méthodes correspondantes.

#### `app.component.html`

```html
<div>
  <h1>Compteur : {{ compteur }}</h1>
  <app-increment-button
    (incrementEvent)="incrementerCompteur()"
  ></app-increment-button>
  <app-decrement-button
    (decrementEvent)="decrementerCompteur()"
  ></app-decrement-button>
</div>
```

### Lancer l'Application

Lancez votre application pour voir les composants en action :

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir les boutons d'incrémentation et de décrémentation fonctionnant correctement.

### Explication

- **Composant `IncrementButtonComponent`** : Ce composant émet un événement `incrementEvent` lorsqu'il est cliqué.
- **Composant `DecrementButtonComponent`** : Ce composant émet un événement `decrementEvent` lorsqu'il est cliqué.
- **Composant `AppComponent`** : Ce composant écoute les événements `incrementEvent` et `decrementEvent` et met à jour la valeur du compteur en conséquence.

En suivant ces étapes, vous devriez être en mesure de créer des composants standalone pour l'incrémentation et la décrémentation, et de les intégrer dans le composant principal. Si vous avez des questions ou des problèmes, n'hésitez pas à demander !
