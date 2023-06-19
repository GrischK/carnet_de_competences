# REST API

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les verbes HTTP ✔️
  Les verbes HTTP indiquent le type d'action que l'on souhaite réaliser avec nos données. Les verbes les plus répandus
  sont :
    * GET : recevoir des données
    * POST : envoyer des données
    * PATCH : mettre à jour une donnée existante
    * PUT : mettre à jour une donnée en la remplaçant totalement
    * DELETE : supprimer des données

- les statuts HTTP ✔️
  C'est un code numérique qui permet d'indiquer le statut de la réponse à une requête.
    * De 100 à 199 : réponse informative
    * De 200 à 299 : réponse de succès
    * De 300 à 399 : message de redirection
    * De 400 à 499 : erreur du client
    * De 500 à 599 : erreur du serveur

- les endpoints ✔️
  Il s'agit des routes d'une API accessibles. Ils fournissent l'emplacement d'une donnée sur le serveur via une URI afin
  que le client puisse interagir avec le serveur.

- CORS ✔️
  Signifie : Cross-Origin Resource Sharing. C'est un mécanisme qui permet d'échanger des fichiers entre domaines
  différents par le biais des en têtes HTTPS.
  Par exemple, la communication entre le front et le back sera bloquée si elles ne partagent pas le même hôte / port. Il
  faudra autoriser les requêtes au niveau du back.

- la nomenclature recommandée pour les routes ✔️
  Il existe quelques bonnes pratiques couramment utilisées pour nommer les routes REST :

    * Utiliser des noms intuitifs et simples.
      exemple : "/utilisateurs" pour représenter la collection d'utilisateurs

    * Éviter les acronymes.
      exemple : "/articles" au lieu de "/art" pour représenter une collection d'articles

    * Utiliser des lettres minuscules.
      exemple : "/clients" au lieu de "/Clients" pour représenter la collection de clients

    * Éviter les caractères spéciaux, car ils peuvent avoir d'autres significations que celles attendues.
      exemple : "/commandes" plutôt que "/commandes!" pour représenter la collection de commandes.

    * Utiliser le slash ("/") comme séparateur entre les éléments.
      exemple : "/utilisateurs/1" pour représenter un utilisateur spécifique avec l'ID 1.

    * Utiliser le tiret ("-") comme séparateur de mot.
      exemple : "/articles/populaires" au lieu de "/articles_populaires" pour représenter les articles populaires.

    * Utiliser le camelCase pour les paramètres.
      exemple : "/articles?categorie=technologie" pour filtrer les articles par catégorie.

    * Éviter les extensions de fichier.
      exemple : "/images" plutôt que "/images.jpg" pour représenter la collection d'images.

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```sh
app.use(cors({ origin: "http://localhost:3000" }));

app.post("/wilders", wildersController.create);
app.get("/wilders", wildersController.read);
app.get("/wilders/:id", wildersController.readOne);
app.patch("/wilders/:id", wildersController.update);
app.delete("/wilders/:id", wildersController.delete);
app.post("/wilders/:wilderId/skills", wildersController.addSkill);
app.delete("/wilders/:wilderId/skills/:skillId", wildersController.removeSkill);
app.patch("/wilders/:wilderId/skills/:skillId", wildersController.updateGrade);
```

```typescript
const wildersController: IController = {
// méthode read qui est en charge de renvoyer toutes les entités Wilders de la BDD
    read: async (req, res) => {
// trycatch pour gérer les erreurs
        try {
// appel asynchrone qui requête notre BDD pour récupérer toutes les entités Wilders
            const allWilders = await dataSource.getRepository(Wilder).find();
// si aucune erreur, renvoi de la réponse avec un status code de 200 (succès) et un body JSON avec les skills
            res.status(200).send({message: "Success", wilders: allWilders});
        } catch (error) {
// en cas d'erreur, envoi de la réponse avec un status code 500 (internal server error) et un body JSON avec un message d'erreur
            res.status(500).send({message: "Error while getting wilders"});
        }
    },
};
```

### Utilisation dans un projet ✔️

[lien github](https://github.com/WildCodeSchool/alrj/blob/develop/backend/src/router.js)

Description : Projet de soutenance pour le Titre de Développeur Web et Web Mobile

### Utilisation en production si applicable❌

### Utilisation en environement professionnel ❌ 

## 🌐 J'utilise des ressources

### Titre
- [developper mozilla](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction)
- Documentation de Developper Mozilla
- [tutoriel](https://www.digitalocean.com/community/tutorials/build-a-restful-api-using-node-and-express-4)
- Tutoriel pour développer une API rest avec Node et Express
- [express](https://expressjs.com/fr/starter/installing.html)
- Documentation d'Express

## 🚧 Je franchis les obstacles

### Point de blocage ️

## 📽️ J'en fais la démonstration
