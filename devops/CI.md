# Integration continue

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les enjeux de l'intégration continue ✔️

  Ils consistent à intégrer régulièrement et automatiquement les modifications de code effectuées par les développeurs, puis à exécuter des tests automatiques pour vérifier l'intégrité du code.
  Elle permet :
    * l'amélioration de la qualité du code
    * la détection précoce des erreurs
    *  la réduction des risques
    * l'accélération du développement 

- la mise en place d'une github action ✔️

  Github action est une fonctionnalité intégrée à GitHub qui consiste à créer un flux de travail automatisé, déclenché par des événements spécifiques tels que les Pull Request (PR), pour exécuter par exemple des tests.

## 💻 J'utilise

### Un exemple personnel commenté ✔️

```yaml
name: jest-ci

# Evénement déclencheur 
on: push

jobs:
  # Définition des jobs
  test-front:
    runs-on: ubuntu-latest
    steps:
      # Configuration des actions
      - name: Check out code
        uses: actions/checkout@v2
      - name: Goto client and run tests
        run: cd client && npm i && npm test
  docker:
    needs: test-front
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    steps:
      -
        name: Set up QEMU
        uses: docker/setup-qemu-action@v2
      -
        name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v2
      -
        name: Login to Docker Hub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      -
        name: Build and push
        uses: docker/build-push-action@v4
        # Gestion des dépendances et des variables
        with:
          push: true
          context: "{{defaultContext}}:server"
          tags: grischk/quete1902
```

### Utilisation dans un projet ✔️

- [Projet Mapado](https://github.com/WildCodeSchool/2209-wns-adleman-mapado)
  Description : Projet de soutenance au Titre de Concepteur Développeur d'Applications

### Utilisation en production si applicable ❌

### Utilisation en environnement professionnel ❌ 

## 🌐 J'utilise des ressources

### Titre

- [GitHub](https://docs.github.com/fr/actions)
  Documentation GitHub
- [Article Red Hat](https://www.redhat.com/fr/topics/devops/what-is-ci-cd)
  Article sur la CI/CD

## 🚧 Je franchis les obstacles

### Point de blocage ✔️

## 📽️ J'en fais la démonstration

- J'ai écrit un [tutoriel]() ❌ ️
- J'ai fait une [présentation]() ❌
