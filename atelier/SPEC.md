# SPEC — Comportements attendus de Cap Web

Chaque critère indique un comportement observable et la manière de le vérifier. Les vérifications correspondent aux tests du projet.

1. Quand un message est vide ou ne contient que des espaces, Cap Web le refuse avec une erreur.
   - Vérifié par : le test `refuse le vide et les espaces seuls` dans `tests/contrat/brain.contrat.test.js` ; essayer `validateMessage('')` et `validateMessage('   ')` : `ok` doit valoir `false`.

2. Quand un message contient 250 caractères après suppression des espaces autour, Cap Web l'accepte ; à 251 caractères, il le refuse.
   - Vérifié par : les tests `accepte 250 caractères et refuse 251` et `mesure la longueur après avoir retiré les espaces` dans `tests/contrat/brain.contrat.test.js` ; les résultats attendus sont respectivement `ok: true` puis `ok: false`.

3. Quand on écrit `salut`, `aide` ou `test` avec des majuscules et des espaces autour, Cap Web donne la même réponse que pour le mot normalisé.
   - Vérifié par : le test `ignore la casse et les espaces autour` dans `tests/contrat/brain.contrat.test.js` ; comparer par exemple `replyTo('  SALUT ')` avec `replyTo('salut')`.

4. Quand on entre un message que Cap Web ne reconnaît pas, il affiche une réponse de repli différente des réponses à `salut`, `aide` et `test`.
   - Vérifié par : le test `répond à une phrase inconnue par un repli distinct` dans `tests/contrat/brain.contrat.test.js` ; comparer `replyTo('parle-moi de la météo')` aux trois réponses connues.

5. Quand Cap Web affiche la conversation, il insère les messages comme du texte et non comme du HTML interprété.
   - Vérifié par : le test `view.js affiche du texte et ne décide pas des réponses` dans `tests/contrat/brain.contrat.test.js` ; vérifier que `view.js` utilise `textContent` et non `innerHTML`, `outerHTML` ou `insertAdjacentHTML`.

Pour exécuter les tests : depuis le dossier `atelier`, lancer `npm test`.
