# Langage Javascript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les `structures` de base du langage ✔️

  Javascript est un langage de script ayant plusieurs types primitifs (number, string, bool, null, undefined...) et non primitifs (object). 
Cependant ,il n'est pas nécessaire de déclarer le type d'une variable avant de l'utiliser.


- les normes `ecmascript` ✔️

  Ensemble de normes qui définissent les standards du langage Javascript. La dernière version majeure est ES6. Chaque nouvelle version apporte des nouvelles fonctionnalités, mots clé ou structures.
Exemple : les variables étaient déclarées préalablement avec le mot clé 'var'. De nouvelles implémentations dans les normes javascript enrichissent la façon de déclarer une variable, avec 'let' et 'const'.

- l'utilisation de l'`asynchrone` ✔️

  La programmation asynchrone implique que l'exécution du code n'attend pas d'une fonction qu'elle délivre sa réponse avant d'exécuter la suite du code. En effet, javascript s'exécute de manière synchrone, ce qui signifie que chaque ligne de code est exécutée dans l'ordre et que l'exécution attend la fin d'une opération avant de passer à la suivante.
L'asynchronisme est donc la capacité du langage à effectuer des opérations sans bloquer l'exécution du reste du code.
Exemple : on peut attendre la fin de l'exécution d'une fonction qui prend du temps pour ensuite utiliser son résultat grâce aux mots clés 'async' et 'await'.

- les spécifités du mot-clef `this` ✔️

  C'est un mot clé faisant référence à l'instance de l'objet utilisé. Notamment utilisé en Programmation Orientée Objet (POO) et dans les constructeurs des class component. 
Exemple : dans une classe, 'this' fera référence à l'instance de cette classe.

## 💻 Je code en Javascript

### Un exemple de code commenté ✔️

```javascript
    const cities = [
      "Bordeaux",
      "Montréal",
      "Stockholm",
      "Lisbonne",
      "Belfast",
      "Prague",
    ];

    getById: async (req, res) => {
        try {
            // récupération de la donnée
            const wilder = await datasource.getRepository(Wilder).findOne({
                where: { id: parseInt(req.params.id, 10) },
                relations: { grades: { skill: true } },
            });
            // conditionnement des données
            if (wilder !== null)
                res.send({
                    ...wilder,
                    grades: undefined,
                    skills: wilder?.grades.map((g) => ({
                        id: g.skill.id,
                        name: g.skill.name,
                        vote: g.votes,
                    })),
                });
            // traitement de la donnée non trouvée
            else res.status(404).send("Wilder not found");
        } catch (err) {
            // traitement de l'erreur
            console.error(err);
            res.send("error while reading wilder");
        }
    }
    
    const wilder = {
        name: "Simon",
        age: 30,
        language: "javascript",
        greet: function() {
            console.log(`Hello, je m'appelle ${this.name}, j'ai ${this.age} ans et je suis fan de ${this.language}.`);
        }
    };

    person.greet(); // Affiche: Hello, je m'appelle Smon, j'ai 30 ans et je suis fan de javascript.
```

### Utilisation dans un projet ✔️

- [lien github](https://github.com/GrischK/JS-Katas).

  Description : Katas JS

### J'ai utilisé ce langage en production ❌

### J'ai utilisé ce langage en environnement professionnel ✔️

Description : Utilisation de javascript pour créer des composants du design system

## 🌐 J'utilise des ressources

### Titre

- [MDN](https://developer.mozilla.org/fr/docs/Web/JavaScript).
  Ressource MDN sur les principes de javascript

- [JavaScript Reference](https://devdocs.io/javascript/).
  Documentation javascript sur les méthodes, fonctions...

- [w3schools](https://www.w3schools.com/jsref/default.asp).
  Exemples javascript

## 🚧 Je franchis les obstacles

### Point de blocage ✔️

## 📽️ J'en fais la démonstration

- J'ai écrit un [tutoriel]() ❌
- J'ai fait une [présentation]() ❌ 

