# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- l'état (_state_) pour contrôler l'affichage d'un composant ✔️

  Le *state* permet de rendre notre composant React dynamique en permettant à ses données internes de changer en réponse aux interactions de l'utilisateur, aux événements ou à d'autres facteurs. Cela facilite la création d'interfaces réactives et interactives.

- les composants enfants et les _props_ qu'on leur passe ✔️

  Les composants enfants en React sont des sous-composants qui héritent des propriétés (props) transmises par leur composant parent pour recevoir des données spécifiques.

- le déclenchement d'instructions en fonction des actions de l'utilisateur ✔️

  Il se réalise grâce à la gestion des événements, où des fonctions spécifiques sont exécutées en réponse à des interactions utilisateur telles que des clics, des saisies de texte, etc... (exemple : onSubmit, onClick, ...)

- le déclenchement d'instructions en fonction de l'étape du cycle de vie du composant ou du changement de valeur de ses props ✔️

  L'utilisation de 'useEffect' en React permet d'exécuter des instructions spécifiques en réponse à des changements d'état, de props ou d'autres événements liés à un composant. 
'useEffect' prend en premier paramètre une fonction (pour exécuter des instructions) et un tableau de dépendance en deuxième paramètre. Ces instructions vont s'exécuter à chaque modification de ces dépendances excepté si le tableau est vide. Dans ce cas les instructions ne s'exécuteront qu'une seule fois au moment du rendu du component.

- l'usage d'un reducer (_useReducer_) pour gérer un état composé dans un composant ❌

- l'état stocké dans un composant avec un _context provider_ et accessible dans ses descendants via `useContext` ✔️

  En utilisant un *context provider* en React, l'état peut être stocké dans un composant et accessible dans ses descendants via 'useContext'. Cela offre une gestion centralisée des données partagées sans avoir besoin de les propager explicitement de parent à enfant via les prop.

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```javascript
  import React, { useState, useEffect } from 'react';
  
  const Counter = ({text}) => {
  // On déclare un état local "count" avec une valeur initiale de 0 et une fonction "setCount" pour le mettre à jour
  const [count, setCount] = useState(0);
  
  useEffect(() => {
  // Cette fonction sera exécutée après chaque rendu du composant
  console.log("Le composant a été rendu.");
  // On peut effectuer d'autres opérations ici, comme la récupération de données depuis une API, l'abonnement à des événements, ...
  });

  // Incrémente la valeur de "count" en utilisant la fonction "setCount"
  const handleIncrement = () => {
  setCount(count + 1);
  };

  // Décrémente la valeur de "count" en utilisant la fonction "setCount"
  const handleDecrement = () => {
  setCount(count - 1);
  };
  
  return (
  <div>
    <h2>Compteur: {count}</h2>
    {/* Affiche la valeur actuelle de "count" */}
    <button onClick={handleIncrement}>Incrémenter</button>
    {/* Appelle la fonction "handleIncrement" lors du clic sur le bouton */}
    <button onClick={handleDecrement}>Décrémenter</button>
    {/* Appelle la fonction "handleDecrement" lors du clic sur le bouton */}
    <p>Ceci est un texte passé en prop: {text}</p>
    {/* Affiche la valeur de la prop "customProp" passée depuis le parent */}
  </div>
  );
  };
  
  export default ExampleComponent;
```

### Utilisation dans un projet ✔️

- [Projet Mapado](https://github.com/WildCodeSchool/2209-wns-adleman-mapado)
  Description : Projet de soutenance au Titre de Concepteur Développeur d'Applications

### Utilisation en production si applicable ❌

### Utilisation en environnement professionnel ✔️

Description : Utilisation dans différents projets professionnels comme la création de composants pour le Design System

## 🌐 J'utilise des ressources

### Titre

- [Documentation React](https://fr.legacy.reactjs.org/docs/getting-started.html)
  Documentation officielle de React

- [Documentation React](https://react.dev/)

- [Documentation Developer Mozilla](https://developer.mozilla.org/fr/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started)
  Documentation MDN

## 🚧 Je franchis les obstacles

### Point de blocage ✔️

## 📽️ J'en fais la démonstration

- J'ai écrit un [tutoriel]() ❌ 
- J'ai fait une [présentation]() ❌ 
