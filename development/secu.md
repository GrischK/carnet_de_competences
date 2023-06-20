# Sécurité dans le développement Web

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- Le rôle de l'OWASP ✔️

  OWASP est l'acronyme d'Open Web Application Security Project. C'est une communauté mondiale qui définit les standards
  de sécurité du web. Elle fournit des ressources pour aider les professionnels et les organisations à créer des
  applications Web plus sécurisées.

- Les injections SQL ✔️

  C'est une technique d'attaque où des données non validées sont insérées dans des requêtes SQL. Elles permettent
  d'exécuter du code SQL non autorisé, pour accéder, modifier ou supprimer des données sensibles.
  Pour s'en prémunir, on peut mettre en place plusieur éléments :
    * validation des données d'entrée
    * utilisation de requêtes préparées
    * mise en place d'une gestion des privilèges appropriée
    * maintenance des logiciels à jour

- XSS ✔️

  Une faille XSS (Cross-Site Scripting) permet d'injecter du code script malveillant dans des pages Web. Les attaquants
  peuvent dès lors exécuter des actions nuisibles sur les navigateurs des utilisateurs.
  Ces failles peuvent provoquer :
    * le vol de données
    * la falsification de contenu
    * le détournement de sessions utilisateur

  Voici quelques éléments pour s'en protéger :
    * valider et échapper les données
    * utiliser des protections au niveau du navigateur
    * filtrer et valider côté serveur

- CRSF ✔️

  Acronyme de Cross-Site Request Forgery, et désigne une attaque où des actions non autorisées sont effectuées sur des
  utilisateurs authentifiés via des requêtes forgées.
  Pour contrer les attaques CRSF, il existe 2 moyens principaux :
    * implémenter des jetons CSRF. Ce sont des valeurs uniques générées aléatoirement côté serveur et envoyées au
      client. Elles permettent de renforcer la sécurité d’une application en rendant difficile pour un attaquant de les
      trouver et donc d’exploiter une vulnérabilité CSRF.
    * utiliser l’attribut SameSite sur les cookies

## 💻 J'utilise

### Un exemple personnel commenté ❌

### Utilisation dans un projet ✔️

```typescript
  // Seuls les utilisateurs ayant le rôle "cityAdmin" sont autorisés à effectuer cette opération.
  @Authorized<
  Role > (["cityAdmin"])
  @Mutation(() => Boolean)
  // Vérification du type de l'argument pour se protéger des injections SQL.
  // TypeORM protège contre les injections SQL en effectuant l'échappement des requêtes.
  async
  deleteUser(@Arg("id", () => Int)
  id: number
  ):
  Promise < boolean > {
      const {affected} = await datasource.getRepository(User).delete(id);
      if(affected === 0
  )
  throw new ApolloError("user not found", "NOT_FOUND");
  return true;
}
```

```typescript
  @Mutation(() => String)
  async login(
      @Arg("data"){ email, password }:UserInput,
      @Ctx() ctx: ContextType
  ): Promise<string> {
  // Recherche de l'utilisateur en fonction de l'e-mail
  const user = await datasource
          .getRepository(User)
          .findOne({where: {email}});
  // Vérification des informations d'identification de l'utilisateur
  if(
    user === null || // Vérifie si l'utilisateur n'existe pas
    !user.hashedPassword || // Vérifie si le mot de passe haché de l'utilisateur est manquant
    !(await verifyPassword(password, user.hashedPassword)) // Vérifie si le mot de passe fourni correspond au mot de passe haché de l'utilisateur
    ){
      throw new ApolloError("invalid credentials");
      // Une erreur est lancée si les informations d'identification fournies sont invalides
    }

    // Génération d'un token JWT contenant l'ID de l'utilisateur
    const token = jwt.sign({userId: user.id}, env.JWT_PRIVATE_KEY);

  // Définition d'un cookie contenant le token JWT dans la réponse HTTP
    ctx.res.cookie("token", token, {
      secure: env.NODE_ENV === "production", // Limite l'envoi du cookie uniquement sur une connexion HTTPS en environnement de production
      domain: env.SERVER_HOST, // Spécifie le domaine du cookie
      httpOnly: true, // Rend le cookie accessible uniquement via des requêtes HTTP
  });
  
  return token; // Renvoie le token JWT généré
}
```

- [Projet Mapado](https://github.com/WildCodeSchool/2209-wns-adleman-mapado).

  Description : Projet de soutenance au Titre de Concepteur Développeur d'Applications

### Utilisation en production si applicable ❌

### Utilisation en environnement professionnel ❌ 

## 🌐 J'utilise des ressources

### Titre

- [Site officiel OWASP](https://owasp.org/).

- [Site officiel JWT](https://jwt.io/introduction).
  Introduction aux Tokens JWT

- [MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies).
  Ressource MDN sur les HTTP Cookies

- [Open-classroom](https://openclassrooms.com/fr/courses/7727176-realisez-un-test-dintrusion-web/7917166-attaquez-la-base-de-donnees-avec-les-injections-sql).
  Cours sur les injections SQL

## 🚧 Je franchis les obstacles

### Point de blocage ✔️

## 📽️ J'en fais la démonstration

- J'ai écrit un [tutoriel]() ❌ 
- J'ai fait une [présentation]() ❌ 
