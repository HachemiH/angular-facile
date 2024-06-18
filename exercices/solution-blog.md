# Exercice : Créer une Application de Blog avec des Modules

## Objectif

1. Créer un module pour les articles de blog.
2. Créer un module pour les auteurs de blog.
3. Utiliser ces modules dans l'application principale.

## Étape 1 : Créer un Nouveau Projet Angular

Utilisez Angular CLI pour créer un nouveau projet :

```bash
ng new blog-app
cd blog-app
```

## Étape 2 : Créer le Module des Articles

1. **Générer le Module des Articles**

   ```bash
   ng generate module articles
   ```

2. **Créer un Composant pour la Liste des Articles**

   ```bash
   ng generate component articles/article-list
   ```

3. **Créer un Composant pour les Détails d'un Article**

   ```bash
   ng generate component articles/article-details
   ```

4. **Définir le Composant de Liste des Articles**

   **article-list.component.ts**

   ```typescript
   import { Component } from "@angular/core";

   @Component({
     selector: "app-article-list",
     templateUrl: "./article-list.component.html",
     styleUrls: ["./article-list.component.css"],
   })
   export class ArticleListComponent {
     articles = [
       { id: 1, title: "Mon Premier Article", author: "John Doe" },
       { id: 2, title: "Mon Deuxième Article", author: "Jane Smith" },
     ];
   }
   ```

   **article-list.component.html**

   ```html
   <h2>Liste des Articles</h2>
   <ul>
     <li *ngFor="let article of articles">
       {{ article.title }} par {{ article.author }}
     </li>
   </ul>
   ```

5. **Définir le Composant de Détails d'un Article**

   **article-details.component.ts**

   ```typescript
   import { Component } from "@angular/core";

   @Component({
     selector: "app-article-details",
     templateUrl: "./article-details.component.html",
     styleUrls: ["./article-details.component.css"],
   })
   export class ArticleDetailsComponent {
     article = {
       id: 1,
       title: "Mon Premier Article",
       content: "Ceci est le contenu de mon premier article...",
       author: "John Doe",
     };
   }
   ```

   **article-details.component.html**

   ```html
   <h2>Détails de l'Article</h2>
   <h3>{{ article.title }}</h3>
   <p>{{ article.content }}</p>
   <p>Écrit par {{ article.author }}</p>
   ```

6. **Déclarer les Composants dans le Module des Articles**

   **articles.module.ts**

   ```typescript
   import { NgModule } from "@angular/core";
   import { CommonModule } from "@angular/common";
   import { ArticleListComponent } from "./article-list/article-list.component";
   import { ArticleDetailsComponent } from "./article-details/article-details.component";

   @NgModule({
     declarations: [ArticleListComponent, ArticleDetailsComponent],
     imports: [CommonModule],
     exports: [ArticleListComponent, ArticleDetailsComponent],
   })
   export class ArticlesModule {}
   ```

## Étape 3 : Créer le Module des Auteurs

1. **Générer le Module des Auteurs**

   ```bash
   ng generate module authors
   ```

2. **Créer un Composant pour la Liste des Auteurs**

   ```bash
   ng generate component authors/author-list
   ```

3. **Définir le Composant de Liste des Auteurs**

   **author-list.component.ts**

   ```typescript
   import { Component } from "@angular/core";

   @Component({
     selector: "app-author-list",
     templateUrl: "./author-list.component.html",
     styleUrls: ["./author-list.component.css"],
   })
   export class AuthorListComponent {
     authors = [
       { id: 1, name: "John Doe", email: "john@example.com" },
       { id: 2, name: "Jane Smith", email: "jane@example.com" },
     ];
   }
   ```

   **author-list.component.html**

   ```html
   <h2>Liste des Auteurs</h2>
   <ul>
     <li *ngFor="let author of authors">
       {{ author.name }} ({{ author.email }})
     </li>
   </ul>
   ```

4. **Déclarer le Composant dans le Module des Auteurs**

   **authors.module.ts**

   ```typescript
   import { NgModule } from "@angular/core";
   import { CommonModule } from "@angular/common";
   import { AuthorListComponent } from "./author-list/author-list.component";

   @NgModule({
     declarations: [AuthorListComponent],
     imports: [CommonModule],
     exports: [AuthorListComponent],
   })
   export class AuthorsModule {}
   ```

## Étape 4 : Utiliser les Modules dans l'Application Principale

1. **Importer les Modules dans le Module Principal**

   **app.module.ts**

   ```typescript
   import { NgModule } from "@angular/core";
   import { BrowserModule } from "@angular/platform-browser";
   import { AppComponent } from "./app.component";
   import { ArticlesModule } from "./articles/articles.module";
   import { AuthorsModule } from "./authors/authors.module";

   @NgModule({
     declarations: [AppComponent],
     imports: [BrowserModule, ArticlesModule, AuthorsModule],
     providers: [],
     bootstrap: [AppComponent],
   })
   export class AppModule {}
   ```

2. **Utiliser les Composants dans le Template Principal**

   **app.component.html**

   ```html
   <h1>Mon Application de Blog</h1>
   <app-article-list></app-article-list>
   <app-article-details></app-article-details>
   <app-author-list></app-author-list>
   ```

## Étape 5 : Lancer l'Application

Lancez votre application pour voir les modules en action :

```bash
ng serve
```

Ouvrez votre navigateur et allez à l'adresse `http://localhost:4200`. Vous devriez voir la liste des articles, les détails d'un article, et la liste des auteurs.
