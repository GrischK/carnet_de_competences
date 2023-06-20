# Titre de la compétence

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les différences et points communs entre du code react et du code react native ✔️

  * Différences :
    1. Plateforme cible : React est destiné à être exécuté dans un navigateur web, tandis que le code React Native est utilisé pour créer des applications mobiles natives pour iOS et Android.
    2. Composants : Les composants de React Native sont spécifiques aux plates-formes mobiles et utilisent des éléments d'interface utilisateur natifs tels que ```<View>```, ```<Text>```, ```<Image>```, plutôt que les éléments HTML de React.
    3. Styles : En React, les styles sont généralement définis à l'aide de CSS tandis qu'en React Native, les styles sont définis via une syntaxe similaire à CSS mais adaptée aux styles natifs des plateformes mobiles.
    4. Interaction avec les périphériques : En React Native, on peut accéder aux fonctionnalités natives des périphériques telles que la caméra, les contacts, le GPS, en utilisant des API spécifiques à chaque plateforme. En React, on doit généralement utiliser des API web standardisées.

  * Points communs :
    1. Syntaxe et structure : Les deux utilisent une syntaxe similaire basée sur javaScript et adoptent une structure basée sur des composants réutilisables.
    2. Gestion d'état : Les 2 offrent des solutions pour la gestion de l'état, notamment 'useState' et 'useEffect', ainsi que la possibilité de passer des props entre composants.
    3. Réutilisation : Les concepts de réutilisabilité des composants et de modularité sont communs aux deux frameworks, permettant de construire des interfaces utilisateur modulaires et scalables.
    4. Écosystème : Les 2 bénéficient de l'écosystème de React, y compris les bibliothèques tierces, les outils de développement et les communautés de développeurs actives.

- ce que devient et comment est interprêté le code javascript dans une application react native ✔️

  Dans une application React Native, le code javaScript est interprété par le runtime de React Native qui communique avec les composants natifs des plateformes iOS et Android pour le rendu et l'interaction de l'interface utilisateur.

- les avantages et inconvénients de react native ✔️

  Les avantages et les inconvénients de React Native peuvent varier en fonction des besoins spécifiques du projet. 

    * Avantages :
      1. Développement multiplateforme : Permet de créer des applications pour iOS et Android à partir d'un codebase commun, réduisant ainsi les efforts de développement.
      2. Réutilisation du code : Les composants peuvent être partagés entre les applications iOS et Android, ce qui permet un développement plus rapide et une maintenance simplifiée.
      3. Performances élevées : Utilise des composants natifs pour le rendu de l'interface utilisateur, offrant des performances proches des applications natives.
      4. Écosystème de React : Bénéficie de l'écosystème solide de React, de la grande communauté de développeurs, du nombre important de bibliothèques tierces et des outils de développement efficaces.

    * Inconvénients : 
      1. Limitations d'accès aux fonctionnalités natives : Certaines fonctionnalités spécifiques peuvent nécessiter l'écriture de modules natifs personnalisés ou l'utilisation de bibliothèques.
      2. Performances limitées pour les animations complexes : Elles peuvent être moins fluides que dans les applications natives, en raison des limitations imposées par le pont de communication javaScript-native.
      3. Taille de l'application : Les applications React Native peuvent être plus volumineuses que leurs équivalents natifs en raison de l'inclusion du runtime javaScript et des dépendances associées.
      4. Dépendance à la stabilité de React Native : Les mises à jour de React Native peuvent introduire des problèmes de compatibilité, nécessitant une maintenance régulière de l'application.
      
- la différence entre react native et expo ✔️

  React Native est un framework qui permet de développer des applications mobiles natives en utilisant javaScript et React qui offrent une flexibilité et des performances avancées.
  Expo est un framework basé sur React Native qui simplifie le développement en fournissant des outils supplémentaires. Il permet notamment un développement rapide et facile, mais avec certaines limitations en termes de personnalisation et de performances avancées.

- les principales briques qui composent react native (core components) ✔️

  Les Core Components (Composants de base) de React Native comprennent un ensemble de composants d'interface utilisateur pré-construits, qui correspondent aux éléments d'interface utilisateur natifs des plateformes iOS et Android. Parmi ces composants, on retrouve des éléments tels que ```<View>```, ```<Text>```, ```<Image>```, ```<Button>```, ```<ScrollView>``` qui remplacent les éléments HTML de React.

- comment écrire du style en react native ✔️

  React Native utilise des objets javaScript pour définir les styles. Les propriétés de style sont également légèrement différentes entre les deux frameworks. On utilisera par exemple la notation camelCase.

  ```javascript
  const styles = StyleSheet.create({
  container: {
    position: 'relative',
    flex: 1,
    backgroundColor: 'white',
  },
  text: {
    textAlign: 'center',
    fontSize: 12,
  },
  });
  ```
- comment est géré le layout en react native ✔️

  React Native utilise le modèle de mise en page flexbox, similaire au CSS, pour contrôler la disposition des éléments.

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```javascript
import {StatusBar} from 'expo-status-bar';
import { FlatList, StyleSheet, TextInput, View, Text } from 'react-native';
import {useCitiesQuery} from "../gql/generated/schema";
import CityListItem from "../components/CityListItem";
import React from "react";


export default function CitiesScreen({navigation}) {
    const [text, onChangeText] = React.useState('');

    const {data} = useCitiesQuery();
    const cities = data?.cities || [];


    return (
    // Création de la structure de notre page avec la balise View
    <View style={styles.container}>
        <StatusBar/>
        {/* Création du champ de texte avec la balises Text */}
        <TextInput
            style={styles.input}
            onChangeText={onChangeText}
            value={text}
            placeholder={"Recherchez un ville"}>
        </TextInput>
        {/* Création du champ de texte avec la balises Text */}
        <Text>Home Screen</Text>
        {/* Création d'une liste d'éléments avec la balise FlatList */}
        <FlatList
            keyExtractor={(item) => item.id.toString()}
            data={cities}
            renderItem={({item}) => <CityListItem navigation={navigation} city={item}/>}
        />
    </View>
    );
    }

    const styles = StyleSheet.create({
    container: {
    flex: 1,
    backgroundColor: '#3270F4',
    alignItems: 'center',
    justifyContent: 'center',
    paddingTop: 10,
    paddingBottom: 10
    },
    mapadoTitle: {
    color: 'white',
    fontSize: 25,
    marginTop: 10,
    paddingBottom: 10,
    },
    user: {
    position: "absolute",
    top: 10,
    right: 10,
    },
    input: {
    backgroundColor: "white",
    width: 220,
    padding: 10,
    marginBottom: 10,
    borderRadius: 10,
    }
});
```

### Utilisation dans un projet ✔️

- [Projet Mapado](https://github.com/WildCodeSchool/2209-wns-adleman-mapado)
  Description : Projet de soutenance au Titre de Concepteur Développeur d'Applications

### Utilisation en production si applicable ❌

### Utilisation en environnement professionnel ❌ 

## 🌐 J'utilise des ressources

### Titre

- [Article freecodecamp](https://www.freecodecamp.org/news/react-js-vs-react-native-whats-the-difference/#:~:text=Here's%20the%20main%20difference%20between,%2C%20cross%2Dplatform%20mobile%20applications)
  Présentation des différences entre React et React Native

- [Documentation React Native](https://reactnative.dev/docs/getting-started)
  Documentation de React Native

- [Documentation d'Expo](https://docs.expo.dev/)
  Documentation d'Expo

## 🚧 Je franchis les obstacles

### Point de blocage ✔️

## 📽️ J'en fais la démonstration

- J'ai écrit un [tutoriel]() ❌ 
- J'ai fait une [présentation]() ❌ 
