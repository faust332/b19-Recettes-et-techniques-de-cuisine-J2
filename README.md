# Cap Web

Cap Web est un assistant fictif créé pour apprendre les bases du développement web.

Il permet d'envoyer des messages, d'obtenir des réponses prédéfinies et de demander un conseil aléatoire grâce à une API locale.

## Installation

Le projet nécessite Node.js.

Depuis le dossier `atelier`, installer les dépendances :

```powershell
npm ci
```

## Lancer le projet

Depuis le dossier `atelier` :

```powershell
npm start
```

Puis ouvrir dans le navigateur :

```text
http://127.0.0.1:3000
```

Pour arrêter le serveur :

```text
Ctrl+C
```

## Lancer les tests

Depuis le dossier `atelier` :

```powershell
npm test
```

Pour vérifier également le code avec ESLint :

```powershell
npm run lint
```

## Arborescence du projet

```text
cap-web/
├── atelier/
│   ├── public/
│   │   ├── js/
│   │   │   ├── app.js
│   │   │   ├── brain.js
│   │   │   └── view.js
│   │   ├── index.html
│   │   └── styles.css
│   ├── server/
│   │   └── app.js
│   ├── tests/
│   └── package.json
├── README.md
└── carnet-j2.md
```

### Rôle des principaux fichiers

- `public/index.html` : structure de la page.
- `public/styles.css` : mise en forme et version mobile.
- `public/js/app.js` : fonctionnement de l'interface et appels au serveur.
- `public/js/brain.js` : validation des messages et réponses de Cap Web.
- `public/js/view.js` : affichage de la conversation.
- `server/app.js` : serveur local et routes de l'API.
- `tests/` : tests automatisés du projet.

## Route `/api/conseil`

Le serveur fournit une route :

```text
GET /api/conseil
```

Elle renvoie un conseil aléatoire au format JSON.

Exemple :

```json
{
  "conseil": "Teste ton code régulièrement."
}
```

Dans Cap Web, il suffit d'envoyer :

```text
conseil
```

pour utiliser cette route.

Si le serveur est indisponible, Cap Web affiche un message clair à la place du conseil.