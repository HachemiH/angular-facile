# Exercice 5 : Créer une Application avec des Modules Simples

## Étape 1 : Créer un Nouveau Projet Angular

```bash
ng new my-app
cd my-app
```

## Étape 2 : Créer le Module de Bienvenue

1. **Générer le Module de Bienvenue**

   ```bash
   ng generate module welcome
   ```

2. **Créer un Composant pour le Message de Bienvenue**

   ```bash
   ng generate component welcome/welcome-message
   ```

3. **Définir le Composant de Message de Bienvenue**

   **welcome-message.component.ts**

   ```typescript
   import { Component } from "@angular/core";

   @Component({
     selector: "app-welcome-message",
     templateUrl: "./welcome-message.component.html",
     styleUrls: ["./welcome-message.component.css"],
   })
   export class WelcomeMessageComponent {
     message = "Bienvenue dans notre application !";
   }
   ```

   **welcome-message.component.html**

   ```html
   <h2>{{ message }}</h2>
   ```

4. **Déclarer le Composant dans le Module de Bienvenue**

   **welcome.module.ts**

   ```typescript
   import { NgModule } from "@angular/core";
   import { CommonModule } from "@angular/common";
   import { WelcomeMessageComponent } from "./welcome-message/welcome-message.component";

   @NgModule({
     declarations: [WelcomeMessageComponent],
     imports: [CommonModule],
     exports: [WelcomeMessageComponent],
   })
   export class WelcomeModule {}
   ```

## Étape 3 : Créer le Module de Liste de Courses

1. **Générer le Module de Liste de Courses**

   ```bash
   ng generate module shopping-list
   ```

2. **Créer un Composant pour la Liste de Courses**

   ```bash
   ng generate component shopping-list/shopping-list
   ```

3. **Définir le Composant de Liste de Courses**

   **shopping-list.component.ts**

   ```typescript
   import { Component } from "@angular/core";

   @Component({
     selector: "app-shopping-list",
     templateUrl: "./shopping-list.component.html",
     styleUrls: ["./shopping-list.component.css"],
   })
   export class ShoppingListComponent {
     items = ["Pommes", "Lait", "Pain"];
   }
   ```

   **shopping-list.component.html**

   ```html
   <h2>Liste de Courses</h2>
   <ul>
     <li *ngFor="let item of items">{{ item }}</li>
   </ul>
   ```

4. **Déclarer le Composant dans le Module de Liste de Courses**

   **shopping-list.module.ts**

   ```typescript
   import { NgModule } from "@angular/core";
   import { CommonModule } from "@angular/common";
   import { ShoppingListComponent } from "./shopping-list/shopping-list.component";

   @NgModule({
     declarations: [ShoppingListComponent],
     imports: [CommonModule],
     exports: [ShoppingListComponent],
   })
   export class ShoppingListModule {}
   ```

#### Étape 4 : Utiliser les Modules dans l'Application Principale

1. **Importer les Modules dans le Composant Racine**

   **app.component.ts**

   ```typescript
   import { Component } from "@angular/core";
   import { WelcomeModule } from "./welcome/welcome.module";
   import { ShoppingListModule } from "./shopping-list/shopping-list.module";

   @Component({
     selector: "app-root",
     templateUrl: "./app.component.html",
     styleUrls: ["./app.component.css"],
     standalone: true,
     imports: [WelcomeModule, ShoppingListModule],
   })
   export class AppComponent {
     title = "my-app";
   }
   ```

   Dans ce fichier, nous importons les modules "WelcomeModule" et "ShoppingListModule", puis nous les ajoutons au tableau "imports" du décorateur `@Component`. Nous définissons également la propriété "standalone" à "true" pour indiquer que ce composant est un composant standalone.

2. **Utiliser les Composants dans le Template Principal**

   **app.component.html**

   ```html
   <h1>Mon Application</h1>
   <app-welcome-message></app-welcome-message>
   <app-shopping-list></app-shopping-list>
   ```

## Étape 5 : Lancer l'Application

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir le message de bienvenue et la liste de courses.
