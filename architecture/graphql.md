# GraphQL

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- la différence entre REST et GraphQL ✔️

  Une API REST (Representational State Transfer) retourne des données au format JSON, XML ou YAML.
  Une API GraphQL renvoie les données sous la forme d'objets et permet au client de récupérer uniquement les données dont il a besoin contrairement aux API REST.

- les besoins auxquels répond GraphQL ✔️

  REST nécessite l'aménagement d'un endpoint par requête alors que GraphQL permet de tous les regrouper en un seul. La structure de la réponse étant portée par la requête elle-même.
  GraphQL utilise un système de typage et toute les données exposées par l'API sont typées.

- la définition d'un schéma ✔️

  Le schéma permet de définir la structure de la donnée attendue dans l'utilisation d'une API GraphQL. le schema d'une entité Book :

  ```typescript
  type Book {
    title: String
    author: Author
  }
  ```

- Query ✔️
- 
  Une Query est une requête qui a pour objectif la lecture seule des données (équivaut à un GET en API REST).

- Mutation ✔️
- 
  Une Mutation est une requête qui permet de modifier des données (équivalent à du PUT, PATCH, DELETE, POST d'une API REST).

- Subscription ✔️
- 
  Une subscription GraphQL permet de lire de la base de données, mais à la différence des Queries, son résultat suit les variations de la base de données. 
  Elle permet de maintenir une connection active avec le serveur afin de recueillir ses mises à jour par le biais des WebSockets.

## 💻 J'utilise

### Un exemple personnel commenté ✔️

  UserQuery côté frontent.

  ```javascript
  export const GET_ALL_USERS = gql`
  query GetAllUsers {
    getAllUsers {
      id
      firstname
      lastname
      email
      role
    }
  }
  `;
  ```

  UserResolver côté backend (définition de requêtes utilisables)

  ```javascript

  @Resolver(User)
  export class UserResolver {
  
    @Query(() => [User])
    async getAllUsers(): Promise<User[]> {
      const users = await UserController.getAllUsers();
      return users.map((user) => getSafeAttributes(user));
    }
  }
  ```

### Utilisation dans un projet ✔️

[lien github](https://github.com/WildCodeSchool/2209-wns-adleman-mapado)

Description : Projet de soutenance du titre professionnel Concepteur Développeur d'Application

### Utilisation en production si applicable ❌

### Utilisation en environement professionnel ❌

Description :

## 🌐 J'utilise des ressources

https://graphql.org/learn/queries/

### Point de blocage ✔️

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel] ❌ ️
- J'ai fait une [présentation] ❌ 
