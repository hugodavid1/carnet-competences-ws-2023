# Integration continue

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les enjeux de l'integration continue ✔️
- la mise en place d'une github action ✔️

## 💻 J'utilise

### Un exemple personnel commenté ❌ / ✔️

### Utilisation dans un projet ✔️

```yaml
name: Backend # Nom du workflow

on:
  pull_request:
    types: [opened, reopened] # Déclenche le workflow lorsqu'une pull request est ouverte ou réouverte
  push:
    branches:
      - main # Déclenche le workflow sur les push dans la branche main

jobs:
  test:
    runs-on: ubuntu-latest # Exécute ce job sur la dernière version d'Ubuntu
    steps:
      - name: Check out code # Étape pour cloner le code du repository
        uses: actions/checkout@v4 # Utilise l'action officielle pour cloner le repo
      - name: Goto backend and run tests # Étape pour installer les dépendances et exécuter les tests
        run: npm i && npm run test # Exécute npm install et npm test

  docker:
    needs: test # Ce job nécessite que le job "test" soit terminé et réussi
    if: github.ref == 'refs/heads/main' # S'exécute seulement si le push est sur la branche main
    runs-on: ubuntu-latest # Exécute ce job sur la dernière version d'Ubuntu
    steps:
      - name: Checkout # Étape pour cloner le code du repository
        uses: actions/checkout@v4 # Utilise l'action officielle pour cloner le repo github
      - name: Set up QEMU # Configure QEMU pour l'émulation de processeur
        uses: docker/setup-qemu-action@v3 # Utilise l'action officielle pour configurer QEMU
      - name: Set up Docker Buildx # Configure Docker Buildx pour les constructions multi-architecture
        uses: docker/setup-buildx-action@v3 # Utilise l'action officielle pour configurer Buildx
      - name: Login to Docker Hub # Se connecte à Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }} # Utilise le nom d'utilisateur Docker Hub stocké comme secret
          password: ${{ secrets.DOCKERHUB_TOKEN }} # Utilise le mot de passe Docker Hub stocké comme secret
      - name: Build and push # Construit et pousse l'image Docker
        uses: docker/build-push-action@v5
        with:
          context: ./.
          push: true
          tags: ${{ secrets.DOCKERHUB_USERNAME }}/backend:latest, ${{ secrets.DOCKERHUB_USERNAME }}/backend:${{ github.sha }} # Tags pour l'image poussée
```

[lien github](...)

Description :

### Utilisation en production si applicable ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ❌ / ✔️

Description :

## 🌐 J'utilise des ressources

### Titre

- lien
- description

## 🚧 Je franchis les obstacles

### Point de blocage ❌ / ✔️

Description:

Plan d'action : (à valider par le formateur)

- action 1 ❌ / ✔️
- action 2 ❌ / ✔️
- ...

Résolution :

## 📽️ J'en fais la démonstration

- J'ai ecrit un [tutoriel](...) ❌ / ✔️
- J'ai fait une [présentation](...) ❌ / ✔️
