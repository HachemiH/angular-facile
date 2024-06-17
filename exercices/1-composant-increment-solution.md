### Étape 1 : Créer un Nouveau Composant Standalone

Utilisez Angular CLI pour générer un nouveau composant standalone appelé `increment-button` :

```bash
ng generate component increment-button --standalone
```

### Étape 2 : Ajouter la Logique d'Incrémentation

Ouvrez le fichier `increment-button.component.ts` et ajoutez la logique pour émettre un événement lorsque le bouton est cliqué.

#### `increment-button.component.ts`

```typescript
import { Component, Output, EventEmitter } from "@angular/core";

@Component({
  selector: "app-increment-button",
  template: `<button (click)="increment()">Incrémenter</button>`,
  standalone: true,
})
export class IncrementButtonComponent {
  @Output() incrementEvent = new EventEmitter<void>();

  increment() {
    this.incrementEvent.emit();
  }
}
```

### Étape 3 : Émettre un Événement depuis le Composant

La méthode `increment` utilise `this.incrementEvent.emit()` pour émettre l'événement `incrementEvent`.

### Étape 4 : Écouter l'Événement dans le Composant Parent

Ouvrez le fichier `app.component.ts` et importez le composant `IncrementButtonComponent`. Ajoutez une méthode pour incrémenter la valeur du compteur.

#### `app.component.ts`

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
  compteur: number = 0;

  incrementerCompteur() {
    this.compteur++;
  }
}
```

### Étape 5 : Afficher la Valeur Incrémentée

Ouvrez le fichier `app.component.html` et ajoutez le sélecteur du composant `IncrementButtonComponent`. Écoutez l'événement `incrementEvent` et appelez la méthode `incrementerCompteur`.

#### `app.component.html`

```html
<div>
  <h1>Compteur : {{ compteur }}</h1>
  <app-increment-button
    (incrementEvent)="incrementerCompteur()"
  ></app-increment-button>
</div>
```

### Correction Complète

Voici la solution complète pour l'exercice.

#### `increment-button.component.ts`

```typescript
import { Component, Output, EventEmitter } from "@angular/core";

@Component({
  selector: "app-increment-button",
  template: `<button (click)="increment()">Incrémenter</button>`,
  standalone: true,
})
export class IncrementButtonComponent {
  @Output() incrementEvent = new EventEmitter<void>();

  increment() {
    this.incrementEvent.emit();
  }
}
```

#### `app.component.ts`

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
  compteur: number = 0;

  incrementerCompteur() {
    this.compteur++;
  }
}
```

#### `app.component.html`

```html
<div>
  <h1>Compteur : {{ compteur }}</h1>
  <app-increment-button
    (incrementEvent)="incrementerCompteur()"
  ></app-increment-button>
</div>
```

### Lancer l'Application

Lancez votre application pour voir le composant en action :

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir le bouton d'incrémentation fonctionnant correctement.

### Explication

- **Composant `IncrementButtonComponent`** : Ce composant émet un événement `incrementEvent` lorsqu'il est cliqué.
- **Composant `AppComponent`** : Ce composant écoute l'événement `incrementEvent` et incrémente la valeur du compteur en conséquence.

En suivant ces étapes, vous devriez être en mesure de créer un bouton d'incrémentation avec succès. Si vous avez des questions ou des problèmes, n'hésitez pas à demander !
