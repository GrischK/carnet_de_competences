# TypeScript

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- l'intérêt de TypeScript dans l'IDE ✔️

  Permet d'ajouter un typage fort sur les variables. Cela permet de détecter les erreurs de compilation et de faciliter
  la résolution de bugs.

- les types de bases ✔️

    * Number
    * String
    * Boolean
    * Array (ex: number[] désigne un table de number)
    * Enum
    * Any
    * Void
    * types pour différents évènements (MouseEvent, InputEvent...)

- comment et pourquoi étendre une interface ✔️

  Une interface permet de définir le typage d'une ou plusieurs données et de pouvoir utiliser ce typage partout dans le
  code (à condition d'exporter l'interface). Ainsi, une interface étendue pourra rajouter des spécificités à une classe
  à portée plus large.

- les classes et les decorators ✔️

  Les classes permettent de décrire une entité. Elles contiennent un constructor qui est la fonction appelée lors de
  l'instanciation de cette classe.
  Les decorators se placent au-dessus des propriétés / méthodes et permettent d'ajouter des annotations. Ils commencent
  généralement par un @ suivi du nom du décorateur.

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```typescript
  interface InterfaceB extends InterfaceA {
      // étend les méthodes et propriété de l'InterfaceA, et en ajoute les suivantes
      newProp: number,
  
      newMeth(x: string)
  
      =>
      string
  }
```

```typescript
      // Définition de l'entité Wilder avec l'annotation @Entity()
  @Entity()
  export class Wilder implements IWilder {
      // Annotation pour indiquer que la propriété "id" est générée automatiquement comme clé primaire
      @PrimaryGeneratedColumn()
      id: number;
  
      // Annotation pour indiquer que la propriété "name" est une colonne de type string
      @Column()
      name: string;
  
      @Column()
      city: string;
  
      @Column()
      description: string;
  
      // Annotation pour indiquer que la propriété "avatar" est une colonne de type string
      // Cette propriété est optionnelle, car elle est suivie du symbole "?"
      @Column()
      avatar?: string;
  
      // Annotation pour indiquer une relation One-to-Many avec l'entité Grade
      // La fonction callback spécifie la relation avec la propriété "wilder" dans l'entité Grade
      // L'option "cascade: true" indique que les opérations de cascade sont activées pour cette relation
      @OneToMany(() => Grade, (grade) => grade.wilder, {
          cascade: true,
      })
      grades: Grade[];
  }
```

```typescript
  import NavBar from "./NavBar.tsx";
  // Importation du type ReactNode depuis la bibliothèque "react"
  import {ReactNode} from "react";

  // Définition de l'interface LayoutProps qui spécifie les propriétés attendues pour le composant Layout

  interface LayoutProps {
      children: ReactNode; // La propriété "children" doit être de type ReactNode
  }

  // Définition du composant Layout qui utilise les propriétés spécifiées dans l'interface LayoutProps
  export default function Layout({children}: LayoutProps) {
      return (
          <>
            <NavBar/>
            {children}
          </>
      )
  }
```

### Utilisation dans un projet ✔️

- [Portfolio perso](https://github.com/GrischK/portfolio_animated).

  Description : Portfolio en cours de développement utilisant TypeScript

### Utilisation en production si applicable ❌

### Utilisation en environnement professionnel ✔️

Description : Utilisation de typescript dans différents projets professionnels

## 🌐 J'utilise des ressources

### Titre

- [Typescriptlang](https://www.typescriptlang.org/).
  Documentation officiel de typescript

- [open-classroom](https://openclassrooms.com/fr/courses/8039116-decouvrez-typescript).
  Cours en ligne sur TypeScript

## 🚧 Je franchis les obstacles

### Point de blocage ✔️

## 📽️ J'en fais la démonstration

- J'ai écrit un [tutoriel]() ❌ 
- J'ai fait une [présentation]() ❌ 
