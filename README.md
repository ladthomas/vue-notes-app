# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Vue - Official](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (previously Volar) and disable Vetur


# Vue 3 Notes

Créer une application de gestion de notes (clone d’Apple Notes) en utilisant Vue, Vite, Vue Router et le localStorage du navigateur.

## Fonctionnalités attendues

Dans ce projet, vous allez devoir créer une application de gestion de notes contenant les fonctionnalités suivantes :

- **Créer une note** : Ajouter une nouvelle note.
- **Afficher une note** : Afficher le contenu d'une note sélectionnée.
- **Modifier une note** : Modifier le contenu d'une note existante.
- **Supprimer une note** : Supprimer une note existante.
- **Compteur de mots** : Afficher le nombre de mots pour chaque note.
- **Date et heure de création** : Enregistrer et afficher la date et l'heure de création d'une note.
- **Date et heure de dernière mise à jour** : Enregistrer et afficher la date et l'heure de la dernière modification d'une note.
- **Sauvegarde des notes** : Utiliser le localStorage pour sauvegarder les notes côté client afin de pouvoir les récupérer en cas de rechargement de la page.

## Contraintes techniques

- **Interface utilisateur** : Créer une interface qui se rapproche le plus possible de l'application Apple Notes, tout en tenant compte des limitations des navigateurs web.
- **Organisation du code** : Utiliser les composants Vue pour organiser le code de manière optimale.
- **Routes** : Chaque note doit avoir sa propre URL (route) pour une navigation facile.

## Interface

Vous pouvez créer l’interface de votre choix. L’essentiel est d’avoir les fonctionnalités attendues. Il est recommandé d’utiliser un framework CSS pour une interface plus agréable et professionnelle.

## Installation

Pour commencer avec ce projet, suivez ces étapes :

1. Clonez le repository :
    ```bash
    git clone https://github.com/votre-utilisateur/votre-repository.git
    cd votre-repository
    ```

2. Installez les dépendances :
    ```bash
    npm install
    ```

3. Démarrez le serveur de développement :
    ```bash
    npm run dev
    ```

4. Construisez le projet pour la production :
    ```bash
    npm run build
    ```

## Utilisation

Après avoir démarré le serveur de développement, ouvrez votre navigateur et accédez à `http://localhost:3000` pour voir l'application en action. Vous pouvez créer, afficher, modifier et supprimer des notes directement depuis l'interface.

## Dépendances

- **Vue 3** : Pour construire les interfaces utilisateur.
- **Vite** : Pour le build et le développement rapide.
- **Vue Router** : Pour gérer les routes de l'application.
- **localStorage** : Pour la persistance des données côté client.

## Contribution

Les contributions sont les bienvenues ! Veuillez suivre les étapes ci-dessous pour contribuer :

1. Fork le repository.
2. Créez une nouvelle branche :
    ```bash
    git checkout -b feature-nouvelle-fonctionnalité
    ```
3. Faites vos modifications et committez :
    ```bash
    git commit -m "Ajout d'une nouvelle fonctionnalité"
    ```
4. Poussez la branche :
    ```bash
    git push origin feature-nouvelle-fonctionnalité
    ```
5. Créez une Pull Request.


