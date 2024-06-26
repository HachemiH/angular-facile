# Composants dans Angular

## Qu'est-ce qu'un Composant ?

Un composant est l'unité de base de l'interface utilisateur dans une application Angular. Chaque composant est une classe qui interagit avec une vue HTML via un ensemble de propriétés et de méthodes. Les composants sont utilisés pour diviser l'application en parties réutilisables et indépendantes.

## Structure d'un Composant

Un composant Angular se compose de trois parties principales :

1. **Template** : Le HTML qui définit la vue.
2. **Style** : Le CSS qui définit l'apparence de la vue.
3. **Logique** : Le TypeScript qui définit le comportement du composant.

### Création d'un Composant

### Utilisation de Angular CLI

Pour créer un composant, vous pouvez utiliser Angular CLI, un outil en ligne de commande qui simplifie le développement Angular. Voici comment créer un composant standalone :

```bash
ng generate component nom-du-composant --standalone
```

Cette commande crée un dossier avec quatre fichiers :

- `nom-du-composant.component.ts` : La classe du composant.
- `nom-du-composant.component.html` : Le template HTML.
- `nom-du-composant.component.css` : Les styles CSS.
- `nom-du-composant.component.spec.ts` : Les tests unitaires (optionnel).

### Exemple de Composant

Voici un exemple de composant simple :

**nom-du-composant.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-nom-du-composant",
  templateUrl: "./nom-du-composant.component.html",
  styleUrls: ["./nom-du-composant.component.css"],
  standalone: true,
})
export class NomDuComposantComponent {
  titre: string = "Bonjour, Angular !";

  afficherMessage() {
    alert("Message affiché depuis le composant !");
  }
}
```

**nom-du-composant.component.html**

```html
<div>
  <h1>{{ titre }}</h1>
  <button (click)="afficherMessage()">Cliquez-moi</button>
</div>
```

**nom-du-composant.component.css**

```css
h1 {
  color: blue;
}
```

#### Utilisation du Composant dans l'Application

Pour utiliser le composant standalone dans l'application, vous devez l'importer dans le composant principal (`app.component.ts`).

**app.component.ts**

```typescript
import { Component } from "@angular/core";
import { RouterOutlet } from "@angular/router";
import { NomDuComposantComponent } from "./nom-du-composant/nom-du-composant.component";

@Component({
  selector: "app-root",
  standalone: true,
  imports: [RouterOutlet, NomDuComposantComponent],
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"],
})
export class AppComponent {
  title = "atelier-angular";
}
```

**app.component.html**

```html
<app-nom-du-composant></app-nom-du-composant>
```

### Lancer l'Application

Enfin, lancez votre application pour voir le composant en action :

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir le contenu de votre composant affiché.

---

## Exercice 1 : Créer un Bouton d'Incrémentation

#### Objectif

Créer un composant standalone pour un bouton d'incrémentation qui émet un événement lorsqu'il est cliqué. Le composant parent doit écouter cet événement et incrémenter une valeur affichée à l'écran.

#### Étapes de l'Exercice

1. **Créer un Nouveau Composant Standalone**
2. **Ajouter la Logique d'Incrémentation**
3. **Émettre un Événement depuis le Composant**
4. **Écouter l'Événement dans le Composant Parent**
5. **Afficher la Valeur Incrémentée**

[Solution Exercice 1](./exercices/1-solution-composant-increment-solution.md)

---

### Exercice 2 : Ajouter un Bouton de Décrémentation

#### Objectif

Créer un composant standalone qui gère à la fois l'incrémentation et la décrémentation de la valeur du compteur. Le composant doit être autonome et réutilisable.

#### Étapes de l'Exercice

1. **Créer un Nouveau Composant Standalone**
2. **Ajouter la Logique d'Incrémentation et de Décrémentation**
3. **Afficher la Valeur Incrémentée et Décrémentée**

[Solution Exercice 2](./exercices/2-solution-composant-increment-decrement-solution.md)
