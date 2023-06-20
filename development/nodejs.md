# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- Comment développer en utilisant un système de *livereloading* (`nodemon` par exemple) ✔️
  
  Les systèmes de *livereloading* permettent de surveiller les fichiers et de redémarrer l'application à chaque fois qu'un fichier est modifié. On peut donc voir les modifications apportées à notre code instantanément sans avoir à redémarrer manuellement l'application.
Pour utiliser nodemon par exemple, il faut :
  * node.js installé sur la machine
  * Initialiser un projet Node.js en exécutant la commande 'npm init'
  * Installer nodemon en tant que dépendance de développement en exécutant la commande 'npm install --save-dev nodemon'
  * Créer un fichier javaScript principal pour votre application, comme 'index.js' par exemple
  * Dans le fichier package.json, ajouter un script "start" qui exécutera l'application à l'aide de nodemon
    Exemple : 
    ```javascript
    "scripts": {
    "start": "nodemon index.js"
    }
    ```

- La connexion de mon application à une base de données avec et sans ORM/ODM (avec `mongodb` puis `mongoose` par exemple) ✔️

  On indique les paramètres de connexion dans un fichier '.env' pour ne pas les exposer et on utilise ces variables d'environnement dans notre configuration de connexion à la base de données :

  * Sans ORM 

  ```javascript
    const database = mysql.createPool({
    host: process.env.DB_HOST, 
    port: process.env.DB_PORT, 
    user: process.env.DB_USER,
    password: process.env.DB_PASSWORD,
    database: process.env.DB_NAME,
    });
    
    const getWilders = (req, res) => {
    database
    .query("select * from wilders")
    .then(([wilders]) => {
    res.json(wilders);
    })
    .catch((err) => {
    console.error(err);
    res.status(500).send("Error retrieving data from database");
    });
    };
  ```

  * Avec un ORM comme typeorm
  
  ```javascript
    import { DataSource } from "typeorm";
    import Wilder from "./entity/Wilder";
    import Skill from "./entity/Skill";
    import Grade from "./entity/Grade";
    
    export default new DataSource({
    type: "postgres",
    host: "db",
    port: 5432,
    username: "postgres",
    password: "postgres",
    database: "postgres",
    synchronize: true,
    entities: [Wilder, Skill, Grade],
    });
  ```
    
  On initie le serveur avec les resolvers pour construire le schéma :

  ```javascript
    const start = async (): Promise<void> => {
    await datasource.initialize();
    
    const schema = await buildSchema({
    resolvers: [WilderResolver, SkillResolver, GradeResolver],
    });
    
    await server.listen().then(({ url }) => {
    console.log(`🚀  Server ready at ${url}`);
    });
    };
    
    void start();
  ```

- Le développement d'une API REST et GraphQL (avec les packages `express` et `graphql` par exemple) ✔️

  On définit une route GET pour l'URL "/api/wilders" dans une application express :

```javascript
    app.get("/api/wilders", WildersController.getAllWilders);
```

  On définit une query en API GraphQL où la fonction getAllWilders du WildersController sera appelée pour récupérer tous les 'wilders' :

```typescript
    @Query(() => [Wilder])
    async getAllWilders(): Promise<Wilder[]> {    
    return await WildersController.getAllWilders();
    }
```

- *Bonus : la manipulation des fichiers système avec `fs` et l'utilisation des streams en NodeJS* ❌ / ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```javascript
  //On exporte la méthode de création de wilder
  exports.createProduct = (req, res, next) => {
    //On récupère le corps de la requête
    const newWilder = req.body;
    //On enregistre le wilder en base de données et on récupère l'erreur si on rencontre un problème lors de l'enregistrement
    newWilder
            .save()
            .then(() => res.status(201).json({ message: "Wilder saved in db" }))
            .catch((error) => res.status(400).json({ error }));
  };
```

### Utilisation dans un projet ✔️

- [Projet Mapado](https://github.com/WildCodeSchool/2209-wns-adleman-mapado)
  Description : CRUD pour les villes, les POI, les catégories et les utilisateurs

### Utilisation en production si applicable ❌

### Utilisation en environnement professionnel ✔️

Description : Création d'un 'proof of concept' (POC) avec nest.js. 

## 🌐 J'utilise des ressources

### Titre

- [Documentation node.js](https://nodejs.org/en/docs)
- [Documentation typeorm](https://typeorm.io/)
- [Documentation nest.js](https://docs.nestjs.com/)

## 🚧 Je franchis les obstacles

### Point de blocage ✔️

## 📽️ J'en fais la démonstration

- J'ai écrit un [tutoriel]() ❌
- J'ai fait une [présentation]() ❌ 
