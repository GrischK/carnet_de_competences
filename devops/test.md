# Tester son application

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les tests unitaires ✔️

  Ils servent à tester individuellement une fonction ou une classe, avec différents cas (succès, échecs, cas limites). Ce sont des tests simples qui doivent respecter les principes de responsabilité unique ou d'encapsulation.
  L'objectif est de s'assurer que chaque unité de code fonctionne comme prévu, de manière isolée, indépendamment des autres parties du système.

- les mocks ✔️

  Ils simulent des données ou reproduisent le comportement d'objets afin de passer des tests sans accéder à des données réelles. Ils permettent d'isoler les dépendances, de contrôler les résultats et de faciliter les tests unitaires ou d'intégration.

- les tests d'intégration ✔️

  Ils succèdent généralement aux tests unitaires. Ils permettent de vérifier une partie du code, comme une fonctionnalité, lorsqu'elle interagit avec d'autres parties du code.
  Exemple : Une requête entrante appelle un Controller, une méthode, qui doit renvoyer une réponse précise. On teste l'ensemble du cheminement plutôt que chaque fonctionnalité. 

- les tests de bout en bout (end to end) ✔️

  Ils permettent de tester le fonctionnement global de l'application, simulant les interactions utilisateurs. On vérifie que l'ensemble fonctionne comme attendu. Ces tests prennent davantage de temps et sont plus coûteux.

- le TDD ✔️

  Acronyme de Test-Driven Development. Désigne une approche basée sur l'écriture des tests unitaires avant d'écrire le code.
  On définit un résultat attendu et on écrit le test associé. Le code est ensuite écrit pour passer le test.

- les tests par snapshot ✔️

  Il s'agit d'une 'photographie' de l'état d'un composant ou de l'application au moment du test. Si des modifications sont apportées par la suite, un nouveau test comparera le résultat obtenu avec le résultat du premier test. Cela permet de vérifier qu'il n'y a pas de régression lors de la modification.

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```typescript
    describe("User resolver", () => {
        describe("create user", () => {
            it("should create user given valid attributes", async () => {
                // Crée un utilisateur en appelant la mutation createUserMutation avec des attributs valides
                const res = await client.mutate({
                    mutation: createUserMutation,
                    variables: {data: {email: "plato@plato.com", password: "Pl@to123"}},
                });
    
                // Vérifie si la propriété "email" est présente dans la réponse
                expect(res.data?.createUser).toHaveProperty("email");
            });
    
            it("should not create user given invalid attributes and return an error", async () => {
                // Vérifie que lorsque des attributs invalides sont fournis, une erreur est renvoyée
                await expect(() => client.mutate({
                    mutation: createUserMutation,
                    variables: {data: {email: "", password: "potato"}}
                })).rejects.toThrowErrorMatchingInlineSnapshot(`"Argument Validation Error"`);
            });
        });
    
        describe("read users", () => {
            it("should return an array", async () => {
                // Insère deux utilisateurs fictifs dans la base de données
                await db
                    .getRepository(User)
                    .insert([{id: 1}, {id: 2}]);
    
                // Effectue une requête pour obtenir la liste des utilisateurs
                const res = await client.query({
                    query: getUsersQuery,
                    fetchPolicy: "no-cache",
                });
    
                // Vérifie si la longueur du tableau d'utilisateurs est de 2
                expect(res.data.users.length).toBe(2);
    
                // Vérifie si le premier utilisateur du tableau a une propriété "id"
                expect(res.data.users[0]).toHaveProperty("id");
            });
        });
    });
```

### Utilisation dans un projet ✔️

- [Projet Mapado](https://github.com/WildCodeSchool/2209-wns-adleman-mapado).
  Description : Projet de soutenance au Titre de Concepteur Développeur d'Applications

### Utilisation en production si applicable ❌ 

### Utilisation en environnement professionnel ❌ / ✔️

Description : Plusieurs tests unitaires et e2e réalisés sur les composants du Design System ou sur les POC.

## 🌐 J'utilise des ressources

### Titre

- [Site officiel Jest](https://jestjs.io/fr/docs/getting-started). 
  Documentation jest et tutoriel

- [Site officiel Nest.js](https://docs.nestjs.com/fundamentals/testing).
  Documentation nest.js et tutoriel pour la mise en place de test pour un POC

## 🚧 Je franchis les obstacles

### Point de blocage ✔️

## 📽️ J'en fais la démonstration

- J'ai écrit un [tutoriel]() ❌
- J'ai fait une [présentation]() ❌ 
