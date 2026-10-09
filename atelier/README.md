# Cap Web

## À quoi sert Cap Web ?

Cap Web est un petit assistant de conversation accessible depuis une page web.
Il répond à des commandes et à des mots reconnus grâce à des règles écrites en JavaScript, sans service d'IA externe.
Il valide les messages, affiche la conversation et conserve son historique dans le navigateur.

## Installer et lancer le projet

Prérequis : **Node.js 24.20.0 ou plus récent** et **npm**.

Ouvrir un terminal dans le dossier `atelier`, puis exécuter les commandes dans cet ordre :

```powershell
npm ci
npm start
```

Ouvrir ensuite http://127.0.0.1:3000/ dans un navigateur. Pour arrêter le serveur, faire **Ctrl+C** dans le terminal.

Pour lancer les tests automatisés depuis le dossier `atelier` :

```powershell
npm test
```

## Les trois modules de `public/js`

- **`brain.js` — les règles :** vérifie qu'un message est du texte, qu'il n'est pas vide et qu'il respecte la limite de 250 caractères après suppression des espaces autour. Il produit une réponse pour les commandes et mots reconnus, ou une réponse de repli pour les autres messages. Il ne manipule pas la page web.
- **`view.js` — l'affichage :** construit les éléments visibles de la conversation et y place les messages comme du texte avec `textContent`. Il ne choisit pas les réponses.
- **`app.js` — la coordination :** écoute le formulaire, appelle `brain.js` pour valider et répondre, puis `view.js` pour afficher. Il gère également le compteur de caractères, l'historique conservé dans `localStorage` et l'effacement de la conversation.
