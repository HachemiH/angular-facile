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
ng generate service welcome
```

Cette commande crée deux fichiers :

- `welcome.service.ts` : La classe du service.
- `welcome.service.spec.ts` : Les tests unitaires (optionnel).

### Exemple de Service

Voici un exemple de service simple qui gère un message de bienvenue :

**welcome.service.ts**

```typescript
import { Injectable } from "@angular/core";

@Injectable({
  providedIn: "root",
})
export class WelcomeService {
  private message: string = "Bienvenue sur notre site !";

  getMessage(): string {
    return this.message;
  }

  setMessage(newMessage: string) {
    this.message = newMessage;
  }
}
```

## Explication du Décorateur `@Injectable`

Le décorateur `@Injectable` est utilisé pour indiquer qu'une classe peut être injectée en tant que dépendance. Voici une explication détaillée de ses propriétés :

- **`@Injectable()`** : Ce décorateur marque la classe comme pouvant être injectée. Cela signifie qu'Angular peut créer une instance de cette classe et l'injecter dans d'autres classes qui en ont besoin.
- **`providedIn: 'root'`** : Cette option indique qu'Angular doit fournir une instance unique de ce service au niveau de la racine de l'application. Cela signifie que le service sera disponible dans toute l'application, et une seule instance sera partagée entre tous les composants et services qui en ont besoin.

## Utilisation d'un Service dans un Composant

Pour utiliser un service dans un composant, vous devez l'injecter dans le constructeur du composant.

### Exemple de Composant Utilisant un Service

**welcome.component.ts**

```typescript
import { Component } from "@angular/core";
import { WelcomeService } from "../welcome.service";

@Component({
  selector: "app-welcome",
  templateUrl: "./welcome.component.html",
  styleUrls: ["./welcome.component.css"],
  standalone: true,
})
export class WelcomeComponent {
  message: string;

  constructor(private welcomeService: WelcomeService) {
    this.message = this.welcomeService.getMessage();
  }

  updateMessage(newMessage: string) {
    this.welcomeService.setMessage(newMessage);
    this.message = this.welcomeService.getMessage();
  }
}
```

**welcome.component.html**

```html
<div>
  <p>{{ message }}</p>
  <button (click)="updateMessage('Bienvenue à tous !')">
    Changer le message
  </button>
</div>
```

## Conclusion

Les services sont un élément clé de l'architecture Angular. Ils permettent de centraliser et de réutiliser la logique métier, de simplifier les composants, et de gérer l'état de l'application de manière efficace. En comprenant comment créer et utiliser des services, vous pouvez construire des applications Angular plus modulaires et maintenables.

---

### Exercice 3 : Séparer les Composants Incrément et Décrément avec un Compteur Partagé

#### Objectif

Créer deux composants standalone distincts : un pour le bouton d'incrémentation et un pour le bouton de décrémentation. Utiliser un service Angular pour partager l'état du compteur entre les composants.

[Solution Exercice 3](./exercices/3-solution-composant-increment-decrement-separes.md)
