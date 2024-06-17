# Introduction aux Services dans Angular

## Qu'est-ce qu'un Service ?

Un service dans Angular est une classe qui encapsule des fonctionnalités ou des données que vous souhaitez partager entre différents composants de votre application. Les services sont utilisés pour organiser et centraliser la logique métier, les appels API, la gestion de l'état, et d'autres fonctionnalités réutilisables.

## Pourquoi Utiliser des Services ?

- **Réutilisabilité** : Les services permettent de réutiliser la même logique dans plusieurs composants.
- **Séparation des Préoccupations** : En déplaçant la logique métier et les appels API dans des services, vous gardez vos composants plus simples et plus faciles à maintenir.

## Création d'un Service

### Utilisation de Angular CLI

Pour créer un service, vous pouvez utiliser Angular CLI, un outil en ligne de commande qui simplifie le développement Angular. Voici comment créer un service :

```bash
ng generate service counter
```

Cette commande crée deux fichiers :

- `counter.service.ts` : La classe du service.
- `counter.service.spec.ts` : Les tests unitaires (optionnel).

### Exemple de Service

Voici un exemple de service simple qui gère un compteur :

**counter.service.ts**

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

## Utilisation d'un Service dans un Composant

Pour utiliser un service dans un composant, vous devez l'injecter dans le constructeur du composant.

### Exemple de Composant Utilisant un Service

**increment-button.component.ts**

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

**increment-button.component.html**

```html
<div>
  <p>Compteur : {{ counterService.compteur }}</p>
  <button (click)="increment()">Incrémenter</button>
</div>
```

## Étapes Complètes pour Créer et Utiliser un Service

1. **Créer un Service** : Utilisez Angular CLI pour générer un service.

   ```bash
   ng generate service counter
   ```

2. **Définir le Service** : Ajoutez la logique métier dans le service.

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

3. **Utiliser le Service dans un Composant** : Injectez le service dans le constructeur du composant et utilisez-le.

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

4. **Ajouter le Template HTML** : Ajoutez le template HTML pour afficher la valeur du compteur et le bouton d'incrémentation.
   ```html
   <div>
     <p>Compteur : {{ counterService.compteur }}</p>
     <button (click)="increment()">Incrémenter</button>
   </div>
   ```

## Conclusion

Les services sont un élément clé de l'architecture Angular. Ils permettent de centraliser et de réutiliser la logique métier, de simplifier les composants, et de gérer l'état de l'application de manière efficace. En comprenant comment créer et utiliser des services, vous pouvez construire des applications Angular plus modulaires et maintenables.

---

### Exercice 3 : Séparer les Composants Incrément et Décrément avec un Compteur Partagé

#### Objectif

Créer deux composants standalone distincts : un pour le bouton d'incrémentation et un pour le bouton de décrémentation. Utiliser un service Angular pour partager l'état du compteur entre les composants.

[Solution Exercice 3](./exercices/3-solution-composant-increment-decrement-separes.md)
