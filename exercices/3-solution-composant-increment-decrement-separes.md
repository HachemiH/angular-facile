# Exercice 3 : Séparer les Composants Incrément et Décrément avec un Compteur Partagé

### Étape 1 : Créer un Service pour le Compteur

Utilisez Angular CLI pour générer un service appelé `counter` :

```bash
ng generate service counter
```

#### `counter.service.ts`

Ouvrez le fichier `counter.service.ts` et ajoutez la logique pour gérer l'état du compteur.

```typescript
import { Injectable } from "@angular/core";

@Injectable({
  providedIn: "root",
})
export class CounterService {
  private _compteur: number = 0;

  get compteur(): number {
    return this._compteur;
  }

  increment() {
    this._compteur++;
  }

  decrement() {
    this._compteur--;
  }
}
```

### Étape 2 : Créer les Composants Standalone

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

### Étape 3 : Ajouter la Logique d'Incrémentation et de Décrémentation

#### `increment-button.component.ts`

Ouvrez le fichier `increment-button.component.ts` et ajoutez la logique pour utiliser le service `CounterService`.

```typescript
import { Component } from "@angular/core";
import { CounterService } from "../counter.service";

@Component({
  selector: "app-increment-button",
  templateUrl: "./increment-button.component.html",
  styleUrls: ["./increment-button.component.css"],
  standalone: true,
})
export class IncrementButtonComponent {
  constructor(public counterService: CounterService) {}

  increment() {
    this.counterService.increment();
  }
}
```

#### `increment-button.component.html`

Ouvrez le fichier `increment-button.component.html` et ajoutez le template HTML pour afficher la valeur du compteur et le bouton d'incrémentation.

```html
<div>
  <p>Compteur : {{ counterService.compteur }}</p>
  <button (click)="increment()">Incrémenter</button>
</div>
```

#### `decrement-button.component.ts`

Ouvrez le fichier `decrement-button.component.ts` et ajoutez la logique pour utiliser le service `CounterService`.

```typescript
import { Component } from "@angular/core";
import { CounterService } from "../counter.service";

@Component({
  selector: "app-decrement-button",
  templateUrl: "./decrement-button.component.html",
  styleUrls: ["./decrement-button.component.css"],
  standalone: true,
})
export class DecrementButtonComponent {
  constructor(public counterService: CounterService) {}

  decrement() {
    this.counterService.decrement();
  }
}
```

#### `decrement-button.component.html`

Ouvrez le fichier `decrement-button.component.html` et ajoutez le template HTML pour afficher la valeur du compteur et le bouton de décrémentation.

```html
<div>
  <p>Compteur : {{ counterService.compteur }}</p>
  <button (click)="decrement()">Décrémenter</button>
</div>
```

### Étape 4 : Utiliser les Composants dans le Composant Parent

Ouvrez le fichier `app.component.ts` et importez les composants `IncrementButtonComponent` et `DecrementButtonComponent`.

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
}
```

### Étape 5 : Ajouter les Sélecteurs des Composants dans le Template Principal

Ouvrez le fichier `app.component.html` et ajoutez les sélecteurs des composants `IncrementButtonComponent` et `DecrementButtonComponent`.

#### `app.component.html`

```html
<div>
  <app-increment-button></app-increment-button>
  <app-decrement-button></app-decrement-button>
</div>
```

### Lancer l'Application

Lancez votre application pour voir les composants en action :

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir les boutons d'incrémentation et de décrémentation fonctionnant correctement et partageant la même valeur du compteur.

### Explication

- **Service `CounterService`** : Ce service gère l'état du compteur et fournit des méthodes pour incrémenter et décrémenter la valeur du compteur.
- **Composant `IncrementButtonComponent`** : Ce composant utilise le service `CounterService` pour incrémenter la valeur du compteur et affiche cette valeur.
- **Composant `DecrementButtonComponent`** : Ce composant utilise le service `CounterService` pour décrémenter la valeur du compteur et affiche cette valeur.
- **Composant `AppComponent`** : Ce composant utilise simplement les composants `IncrementButtonComponent` et `DecrementButtonComponent` sans avoir à gérer l'état du compteur.
