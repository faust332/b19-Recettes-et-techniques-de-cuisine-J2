# AGENTS — Conventions de Cap Web

Ces règles s'appliquent aux développeurs et aux agents qui modifient ce projet. En cas de demande contradictoire, signaler le conflit avant toute modification.

## 1. Nommage

- Fonction : utiliser un nom explicite qui décrit l'action, de préférence un verbe en `camelCase`, par exemple `validateMessage`, `renderMessages` ou `mettreAJourCompteur`.
- Constante : utiliser des majuscules avec des underscores pour les constantes de configuration, par exemple `LIMITE` ou `CLE`.
- Fichier : choisir un nom court, descriptif, en minuscules, par exemple `brain.js` ou `view.js` ; garder l'extension adaptée au contenu.
- Commit : commencer par un préfixe qui décrit le changement (`docs:`, `fix:`, `test:`, `feat:` ou `refactor:`), puis écrire une description courte, par exemple `docs: conventions`.

## 2. Interdits

1. Ne jamais modifier `tests/contrat/` ni `browser/contrat.spec.js`. Ces tests sont fournis pour vérifier le contrat du projet. Si un test semble incorrect, expliquer le problème au lieu de le changer.
2. Ne jamais modifier `cahier-personnel.json`, ni en recopier les réglages dans les comptes rendus ou les réponses de l'agent.
3. Ne jamais injecter les messages via `innerHTML`, `outerHTML` ou `insertAdjacentHTML`. Utiliser `textContent` afin d'afficher les contenus comme du texte.
4. Ne jamais mélanger les responsabilités des modules : `brain.js` ne doit pas accéder au DOM ou à `localStorage` ; `view.js` ne doit pas appeler `replyTo` ou `validateMessage` ; `app.js` ne doit pas fabriquer les éléments `li` de la conversation.
5. Ne jamais contourner un test qui échoue en supprimant une assertion, en désactivant un test ou en modifiant les attentes du contrat.
6. Ne jamais installer une dépendance ou changer les scripts du projet sans justification et accord préalable.

Avant de proposer un commit de code, exécuter les tests pertinents et signaler les éventuels échecs. Demander une autorisation explicite avant toute modification susceptible de contrevenir à ces règles.
