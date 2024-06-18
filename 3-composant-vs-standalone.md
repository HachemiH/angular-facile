# Composant Standard vs Composant Standalone

## Composant Standard

Un composant standard dans Angular doit être déclaré dans un module (`NgModule`). Les modules sont utilisés pour regrouper des composants, des directives, des pipes et des services, et pour organiser l'application en unités fonctionnelles.

### Exemple de Composant Standard

1. **Déclaration du Composant dans un Module**

   **app.module.ts**

   ```typescript
   import { NgModule } from "@angular/core";
   import { BrowserModule } from "@angular/platform-browser";
   import { AppComponent } from "./app.component";
   import { StandardComponent } from "./standard/standard.component";

   @NgModule({
     declarations: [AppComponent, StandardComponent],
     imports: [BrowserModule],
     providers: [],
     bootstrap: [AppComponent],
   })
   export class AppModule {}
   ```

2. **Définition du Composant**

   **standard.component.ts**

   ```typescript
   import { Component } from "@angular/core";

   @Component({
     selector: "app-standard",
     templateUrl: "./standard.component.html",
     styleUrls: ["./standard.component.css"],
   })
   export class StandardComponent {
     message: string = "Composant Standard";
   }
   ```

   **standard.component.html**

   ```html
   <p>{{ message }}</p>
   ```

## Composant Standalone

Un composant standalone est un composant qui peut être utilisé sans être déclaré dans un module. Cette fonctionnalité a été introduite pour simplifier la création et l'utilisation des composants, en particulier dans les applications plus petites ou les projets où la modularité n'est pas aussi critique.

### Exemple de Composant Standalone

1. **Définition du Composant Standalone**

   **standalone.component.ts**

   ```typescript
   import { Component } from "@angular/core";

   @Component({
     selector: "app-standalone",
     templateUrl: "./standalone.component.html",
     styleUrls: ["./standalone.component.css"],
     standalone: true,
   })
   export class StandaloneComponent {
     message: string = "Composant Standalone";
   }
   ```

   **standalone.component.html**

   ```html
   <p>{{ message }}</p>
   ```

2. **Utilisation du Composant Standalone**

   **app.component.ts**

   ```typescript
   import { Component } from "@angular/core";
   import { StandaloneComponent } from "./standalone/standalone.component";

   @Component({
     selector: "app-root",
     standalone: true,
     imports: [StandaloneComponent],
     templateUrl: "./app.component.html",
     styleUrls: ["./app.component.css"],
   })
   export class AppComponent {
     title = "atelier-angular";
   }
   ```

   **app.component.html**

   ```html
   <div>
     <app-standalone></app-standalone>
   </div>
   ```

## Différences Clés

1. **Déclaration dans un Module** :

   - **Composant Standard** : Doit être déclaré dans un module (`NgModule`).
   - **Composant Standalone** : N'a pas besoin d'être déclaré dans un module. Il est autonome.

2. **Simplicité** :

   - **Composant Standard** : Nécessite la gestion des modules, ce qui peut ajouter de la complexité, surtout dans les grandes applications.
   - **Composant Standalone** : Simplifie la création et l'utilisation des composants, en particulier pour les petites applications ou les composants réutilisables.

3. **Utilisation** :
   - **Composant Standard** : Utilisé dans des applications où la modularité et l'organisation en modules sont importantes.
   - **Composant Standalone** : Idéal pour les composants réutilisables, les bibliothèques de composants, ou les petites applications où la gestion des modules n'est pas nécessaire.

## Conclusion

Les composants standalone offrent une manière plus simple et plus directe de créer et d'utiliser des composants dans Angular, sans la nécessité de les déclarer dans un module. Cela peut être particulièrement utile pour les petites applications ou les composants réutilisables. Cependant, pour les grandes applications où la modularité et l'organisation en modules sont importantes, les composants standard restent une pratique courante.

---

# Exercice : Créer un Composant Standard et un Composant Standalone

## Objectif

1. Créer un composant standard (non standalone) pour afficher un message.
2. Créer un composant standalone pour afficher un autre message.

[Solution Exercice 4](./exercices/4-solution-composant-vs-standalone.md)
