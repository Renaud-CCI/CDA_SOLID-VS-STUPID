# Programmation SOLID vs Programmation STUPID 🚀

Bienvenue dans ce cours passionnant où nous allons explorer deux approches opposées de la programmation : **SOLID** et **STUPID**. 

**La programmation SOLID** est un ensemble de principes de conception orientée objet qui favorisent un code plus compréhensible, flexible et maintenable. Ces principes sont largement reconnus et utilisés dans l'industrie du logiciel. Ils sont l'acronyme de **Single Responsibility**, **Open-Closed**, **Liskov Substitution**, **Interface Segregation** et **Dependency Inversion**.

D'un autre côté, nous avons **la programmation STUPID 🙅‍♂️**, qui est exactement le contraire. STUPID est un acronyme pour **Singleton**, **Tight Coupling**, **Untestability**, **Premature Optimization**, **Indescriptive Naming** et **Duplication**. Ce sont des pratiques à éviter pour écrire un code de qualité.

Dans ce cours, nous allons décomposer chaque principe, comprendre pourquoi il est important et comment l'appliquer dans vos projets de programmation. Nous allons également identifier les pièges de la programmation STUPID et comment les éviter.

Que vous soyez un développeur débutant ou expérimenté, ce cours vous donnera des outils précieux pour améliorer votre code et votre processus de développement. Préparez-vous à plonger dans le monde fascinant de la programmation SOLID :muscle: et à dire adieu aux pratiques STUPID ! 🚫

## Cours
[Présentation SOLID vs Stupid](https://docs.google.com/presentation/d/12pJqlgKcQk1-v65I_ifbRRzJGlwcG3cw0hy3A9p619U/edit?usp=sharing)

[Ntier + Clean Architecture](https://docs.google.com/presentation/d/1NQWhYr5Y7tRikUP4DuvCoVVzAakeTdboNDvciyO5rMM/edit#slide=id.p)
## Livecodes
<details>
  
  <summary><b>Séparer le code métier</b></summary>
  
  ```php

  abstract class EloquentRepository implements RepositoryInterface{
      protected string $model = '';
      
      public function setModel($model){
          $this->model = $model;
      }
      
      public function transform(object $data){
          return (array) $data;
      }      
  }

  class QuestionEloquentRepository extends EloquentRepository implements RepositoryInterface
  {
        
      /*PLEIN D'AUTRES METHODES COMMUNES AUX DEUX REPOSITORIES*/
        
      public function save($data)
      {
          //does something
      }
  }

  class AnswerEloquentRepository extends EloquentRepository implements RepositoryInterface
  {

      /*PLEIN D'AUTRES METHODES COMMUNES AUX DEUX REPOSITORIES*/

      public function save($data)
      {
          //does something
      }
  }

  // ARCHI AUTRE FRAMEWORK

  abstract class DoctrineRepository implements RepositoryInterface{}

  class QuestionDoctrineRepository extends DoctrineRepository implements RepositoryInterface
  {
      /*PLEIN D'AUTRES METHODES COMMUNES AUX DEUX REPOSITORIES*/      
      public function save($data)
      {
          //does something
      }
  }

  class AnswerDoctrineRepository extends DoctrineRepository implements RepositoryInterface
  {
      /*PLEIN D'AUTRES METHODES COMMUNES AUX DEUX REPOSITORIES*/
      public function save($data)
      {
          //does something
      }
  }

  //--- DANS MON CONTROLLER ARCHI
  $question = new Question();

  //Si archi Laravel
  $question->save(new QuestionEloquentRepository);

  //Si archi doctrine
  $question->save(new QuestionDoctrineRepository);

  //--- CODE METIER - CODE BUSINESS - CODE DOMAIN

  interface RepositoryInterface{
      public function save();
  }

  class Question 
  {
      public function save(RepositoryInterface $repository)
      {
          $repository->save($this);
      }
  }
  ```
</details>

## Exercices
[Exercices SOLID](https://github.com/G404-CDA/Exercices-SOLID/tree/master)

## Ressources

 - [Préjugés PHP](https://www.youtube.com/watch?v=US9JCsnAVTU)
 - [PHP 8 et Just In Time Compilation](https://www.youtube.com/watch?v=g3RPYtwP1jk)
 - [Clean Code - Refactorisation notions générales](https://refactoring.guru/refactoring/what-is-refactoring)
 - [Les normes PSR](https://www.youtube.com/watch?v=6t-CnYHkGTs)
 - [Bonnes pratiques](https://tainix.fr/article-technique/Bonnes-pratiques-PHP-1-un-code-propre-qui-respecte-les-standards)
 - [Debug](https://blog.jetbrains.com/phpstorm/2018/11/php-cs-fixer-support/)
 - [Code Smell](https://refactoring.guru/refactoring/smells) 
      - [Dry](https://thevaluable.dev/dry-principle-cost-benefit-example/)
      - [Duplicate Code](https://refactoring.guru/smells/duplicate-code)
      - [Classes trop grandes](https://refactoring.guru/smells/large-class)
      - [Longues Methodes](https://refactoring.guru/smells/long-method)
      - [Longue liste de paramètres](https://refactoring.guru/smells/long-parameter-list)
      - [Commentaires trop complexes](https://refactoring.guru/smells/comments)
      - [Data Class](https://refactoring.guru/smells/data-class)
      - [Changements trop complexes](https://refactoring.guru/smells/divergent-change)
      - [Code non utilisé](https://refactoring.guru/smells/speculative-generality)
 - [Refactoring]()
      - [Extraire des méthodes](https://refactoring.guru/extract-method)
      - [Méthodes évidentes trop complexes](https://refactoring.guru/inline-method)
      - [Extraction de variables](https://refactoring.guru/extract-variable)
      - [Remplacer variable temporaire avec une fonction](https://refactoring.guru/replace-temp-with-query)
      - [Nommage de variables temporaires](https://refactoring.guru/split-temporary-variable)
      - [Modifier les paramètres de la fonction](https://refactoring.guru/remove-assignments-to-parameters)
      - [Extraire un objet](https://refactoring.guru/replace-method-with-method-object)
      - [Améliorer ses algorithmes](https://refactoring.guru/substitute-algorithm)
  - [Paralysie d'analyse, OverThinking](https://en.wikipedia.org/wiki/Analysis_paralysis)
  - SOLID
    - [SOLID par l’exemple](https://medium.com/@bdelespierre/solid-par-l-exemple-bdef268fcd36)
    - [SOLID: Les principes à l'origine du succès de Symfony et de vos applications](https://www.youtube.com/watch?v=1a50ZzQUUps)
    - [Becoming a better developer by using the SOLID design principles by Katerina Trajchevska](https://www.youtube.com/watch?v=rtmFCcjEgEw)
    - [SOLID et les design patterns](https://openclassrooms.com/fr/courses/7415611-ecrivez-du-php-maintenable-avec-les-principes-solid-et-les-design-patterns?archived-source=6031956)
  - [DDD + Clean Architecture]
    - [AFUP Day Symfony Zoom sur la «Clean Architecture»](https://www.youtube.com/watch?v=k-bb_DwRDwQ)
    - [The Clean Code Blog](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
    - [Nikoms/clean-architecture-example](https://github.com/Nikoms/clean-architecture-example)
    - [Afup Clean Architecture - Nicolas DE BOOSE](https://www.youtube.com/watch?v=2H1rdx3al_8)
## ⛑️ A connaitre PAR COEUR

### ⚠️ Programmation STUPID
 - **S:** Singleton
 - **T:** Tight Coupling
 - **U:** Untestability
 - **P:** Premature Optimisation
 - **I:** Indescriptive Naming
 - **D:** Duplication

### ⛑️ Programmation SOLID
  **🎯 SOLID EST UN OUTIL ET NON UN BUT !!!**

 - **S:** Séparation des responsabilités
 - **O:** Principe Ouvert / Fermé
 - **L:** Principe de substitution de Liskov
 - **I:** Principe de ségrégation des Interfaces
 - **D:** Principe d'Inversion de contrôle

### ⛑️ Principe de l'architecture Ntier
 - Découpage du code en Couche/Layer
 - **3Tiers :** 
   - Presentation Layer 
   - Business Layer 
   - Data Layer
 - Sur des serveurs / instances différentes pour pouvoir s'échelonner
