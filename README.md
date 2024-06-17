# Angular Facile

Angular 18 Débutant
├── Composants de Base
│ ├── Qu'est-ce qu'un composant ?
│ ├── Création de composants
│ ├── Composants Standalone
│ ├── Templates et Styles
│ └── Cycle de Vie des Composants
│ ├── ngOnInit
│ ├── ngOnChanges
│ ├── ngOnDestroy
│ └── Autres hooks
├── Routing et Navigation
│ ├── Configuration du Routing
│ ├── Navigation entre les Vues
│ └── Routes Protégées
├── Modules
│ ├── Qu'est-ce qu'un module ?
│ ├── Création de modules
│ └── Lazy Loading
├── Data Binding
│ ├── Interpolation
│ ├── One-way Binding
│ ├── Two-way Binding
│ └── Event Binding
├── Directives et Pipes
│ ├── Directives Structurelles
│ ├── Directives d'Attributs
│ └── Pipes
├── Services et Injection de Dépendances
│ ├── Qu'est-ce qu'un service ?
│ └── Injection de Dépendances
├── Formulaires
│ ├── Formulaires Template-driven
│ ├── Formulaires Réactifs
│ └── Validation des Formulaires
├── Communication avec une API
│ ├── Fetch API
│ ├── Requêtes HTTP
│ └── Gestion des Erreurs

## Composants dans Angular

### Qu'est-ce qu'un Composant ?

Un composant est l'unité de base de l'interface utilisateur dans une application Angular. Chaque composant est une classe qui interagit avec une vue HTML via un ensemble de propriétés et de méthodes. Les composants sont utilisés pour diviser l'application en parties réutilisables et indépendantes.

### Structure d'un Composant

Un composant Angular se compose de trois parties principales :

1. **Template** : Le HTML qui définit la vue.
2. **Style** : Le CSS qui définit l'apparence de la vue.
3. **Logique** : Le TypeScript qui définit le comportement du composant.

### Création d'un Composant

#### Utilisation de Angular CLI

Pour créer un composant, vous pouvez utiliser Angular CLI, un outil en ligne de commande qui simplifie le développement Angular. Voici comment créer un composant :

```bash
ng generate component nom-du-composant
```

Cette commande crée un dossier avec quatre fichiers :

- `nom-du-composant.component.ts` : La classe du composant.
- `nom-du-composant.component.html` : Le template HTML.
- `nom-du-composant.component.css` : Les styles CSS.
- `nom-du-composant.component.spec.ts` : Les tests unitaires (optionnel).

#### Exemple de Composant

Voici un exemple de composant simple :

**nom-du-composant.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-nom-du-composant",
  templateUrl: "./nom-du-composant.component.html",
  styleUrls: ["./nom-du-composant.component.css"],
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

### Composants Standalone

Les composants standalone sont une fonctionnalité introduite pour simplifier la création de composants sans avoir besoin de les déclarer dans un module. Voici comment créer un composant standalone :

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-standalone-composant",
  template: `<h1>Composant Standalone</h1>`,
  standalone: true,
})
export class StandaloneComposant {}
```

### Cycle de Vie des Composants

Les composants Angular ont un cycle de vie qui comprend plusieurs étapes. Angular fournit des hooks de cycle de vie que vous pouvez utiliser pour exécuter du code à des moments spécifiques du cycle de vie du composant.

#### Principaux Hooks de Cycle de Vie

- **ngOnInit** : Appelé une fois que le composant est initialisé.
- **ngOnChanges** : Appelé lorsque les propriétés liées aux données changent.
- **ngOnDestroy** : Appelé juste avant que le composant soit détruit.

#### Exemple d'Utilisation des Hooks

```typescript
import { Component, OnInit, OnChanges, OnDestroy, Input } from "@angular/core";

@Component({
  selector: "app-cycle-de-vie",
  template: `<p>{{ message }}</p>`,
})
export class CycleDeVieComponent implements OnInit, OnChanges, OnDestroy {
  @Input() message: string;

  ngOnInit() {
    console.log("Composant initialisé");
  }

  ngOnChanges() {
    console.log("Propriétés changées");
  }

  ngOnDestroy() {
    console.log("Composant détruit");
  }
}
```

### Conclusion

Les composants sont au cœur du développement d'applications Angular. Ils permettent de créer des interfaces utilisateur modulaires et réutilisables. En comprenant la structure des composants, la création de composants standalone, et le cycle de vie des composants, vous serez bien équipé pour développer des applications Angular robustes et maintenables.
