# Introduction aux Modules dans Angular pour les Débutants

## Qu'est-ce qu'un Module ?

Imaginez que vous construisez une grande application Angular. Cette application aura de nombreuses fonctionnalités, comme la gestion des utilisateurs, les notifications, les paramètres, etc. Chacune de ces fonctionnalités peut être composée de plusieurs composants, services, et autres éléments.

Un module dans Angular est comme une boîte qui regroupe tous les éléments (composants, services, etc.) liés à une fonctionnalité spécifique. C'est un moyen d'organiser votre application en groupes logiques.

## Pourquoi Utiliser des Modules ?

1. **Organisation** : Les modules vous aident à garder votre application organisée. Au lieu d'avoir tous vos composants et services dans un seul endroit, vous pouvez les diviser en modules basés sur leurs fonctionnalités.

2. **Réutilisabilité** : Si vous avez une fonctionnalité qui est utilisée à plusieurs endroits dans votre application, vous pouvez la mettre dans un module et réutiliser ce module partout où vous en avez besoin.

3. **Performance** : Les modules permettent de charger les fonctionnalités de votre application à la demande. Cela signifie que lorsqu'un utilisateur visite une partie spécifique de votre application, seul le module correspondant est chargé, ce qui rend votre application plus rapide.

## Comment Créer un Module ?

Pour créer un module, vous utilisez le décorateur `@NgModule`. C'est comme une étiquette que vous mettez sur une classe pour dire à Angular que c'est un module.

```typescript
import { NgModule } from "@angular/core";

@NgModule({
  declarations: [], // Les composants, directives, et pipes qui appartiennent à ce module
  imports: [], // Les autres modules dont ce module a besoin
  exports: [], // Les composants, directives, et pipes que ce module rend disponibles aux autres modules
  providers: [], // Les services dont ce module a besoin
})
export class MyModule {}
```

## Exemple Pratique

Disons que vous voulez créer un module pour la fonctionnalité de gestion des utilisateurs dans votre application.

1. **Créer un Module**

   ```bash
   ng generate module user
   ```

2. **Créer un Composant dans le Module**

   ```bash
   ng generate component user/user-profile
   ```

3. **Déclarer le Composant dans le Module**

   **user.module.ts**

   ```typescript
   import { NgModule } from "@angular/core";
   import { CommonModule } from "@angular/common";
   import { UserProfileComponent } from "./user-profile/user-profile.component";

   @NgModule({
     declarations: [UserProfileComponent],
     imports: [CommonModule],
     exports: [UserProfileComponent],
   })
   export class UserModule {}
   ```

4. **Utiliser le Module dans l'Application**

   **app.module.ts**

   ```typescript
   import { NgModule } from "@angular/core";
   import { BrowserModule } from "@angular/platform-browser";
   import { AppComponent } from "./app.component";
   import { UserModule } from "./user/user.module";

   @NgModule({
     declarations: [AppComponent],
     imports: [BrowserModule, UserModule],
     providers: [],
     bootstrap: [AppComponent],
   })
   export class AppModule {}
   ```

## Modules vs Composants Standalone

Avec l'introduction des composants standalone dans Angular, vous pouvez créer des composants sans avoir à les déclarer dans un module. Cependant, les modules restent utiles pour organiser votre application, surtout quand elle devient grande et complexe.

En tant que débutant, vous pouvez commencer par utiliser des composants standalone pour des fonctionnalités simples et autonomes, et utiliser des modules lorsque vous avez besoin de regrouper des fonctionnalités connexes.

## Conclusion

Les modules sont un moyen d'organiser votre application Angular en groupes logiques de fonctionnalités. Ils vous aident à garder votre code organisé, à réutiliser des fonctionnalités, et à améliorer les performances de votre application.

En comprenant les bases des modules, vous serez en mesure de structurer votre application de manière efficace à mesure qu'elle grandit et devient plus complexe.

---

# Exercice 5 : Créer une Application avec des Modules Simples

## Objectif

1. Créer un module pour afficher un message de bienvenue.
2. Créer un module pour afficher une liste de courses.
3. Utiliser ces modules dans l'application principale.

## Consignes

### Étape 1 : Créer un Nouveau Projet Angular

1. Utilisez Angular CLI pour créer un nouveau projet nommé "my-app".
2. Naviguez dans le dossier du projet.

### Étape 2 : Créer le Module de Bienvenue

1. Générez un nouveau module nommé "welcome" en utilisant Angular CLI.
2. Créez un composant nommé "welcome-message" dans le module "welcome" en utilisant Angular CLI.
3. Dans le fichier "welcome-message.component.ts", définissez une propriété "message" avec le texte "Bienvenue dans notre application !".
4. Dans le fichier "welcome-message.component.html", affichez la propriété "message" dans une balise `<h2>`.
5. Dans le fichier "welcome.module.ts", déclarez le composant "WelcomeMessageComponent" dans le tableau "declarations", exportez-le dans le tableau "exports".

### Étape 3 : Créer le Module de Liste de Courses

1. Générez un nouveau module nommé "shopping-list" en utilisant Angular CLI.
2. Créez un composant nommé "shopping-list" dans le module "shopping-list" en utilisant Angular CLI.
3. Dans le fichier "shopping-list.component.ts", définissez une propriété "items" avec un tableau contenant quelques éléments de courses (par exemple, 'Pommes', 'Lait', 'Pain').
4. Dans le fichier "shopping-list.component.html", affichez le titre "Liste de Courses" dans une balise `<h2>`, puis utilisez une boucle `*ngFor` pour afficher chaque élément de la propriété "items" dans une liste non ordonnée (`<ul>`).
5. Dans le fichier "shopping-list.module.ts", déclarez le composant "ShoppingListComponent" dans le tableau "declarations", importez-le dans le tableau "imports" et exportez-le dans le tableau "exports".

### Étape 4 : Utiliser les Modules dans l'Application Principale

1. Dans le fichier "app.module.ts", importez les modules "WelcomeModule" et "ShoppingListModule", puis ajoutez-les au tableau "imports".
2. Dans le fichier "app.component.html", utilisez les sélecteurs des composants "WelcomeMessageComponent" et "ShoppingListComponent" pour les afficher.

### Étape 5 : Lancer l'Application

1. Utilisez Angular CLI pour lancer l'application.
2. Ouvrez votre navigateur et accédez à l'URL indiquée par Angular CLI.
3. Vérifiez que vous voyez le message de bienvenue et la liste de courses.

[Solution Exercice 5](./exercices/5-solution-modules.md)
