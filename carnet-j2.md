# Carnet de bord · J2

Binôme : b19 · Membres : Thomas KLEMPOUZ-RAMOS, Rayan ZOUAOUI · Nos réglages sont dans `atelier/cahier-personnel.json` : ne les recopiez pas ici.

## Mon positionnement (chacun de vous deux)

Pour chaque notion, chacun écrit « à l'aise » ou « à renforcer ». Ce n'est ni évalué ni classé : c'est votre point de départ pour le bilan individuel de fin de module.

| Notion | Membre 1 : Rayan ZOUAOUI | Membre 2 : Thomas KLEMPOUZ-RAMOS |
|---|---|---|
| Structure HTML | | |
| CSS et responsive | | |
| JavaScript | | |
| DOM et événements | | |
| Git | | |
| Tests | | |

Chacun, en une phrase, son objectif personnel pour J2 et J3.

Membre 1 :

Membre 2 :

## R1 · Les tests automatisés

Les tests rouges du départ, et ce que vous en avez fait :

| Test rouge | Cause trouvée (une phrase) | Fichier | Message du commit `fix:` |
|---|---|---|---|
| ✖ refuse le vide et les espaces seuls (2.6907ms) | Le code vérifiait seulement si le message était vide avant de retirer les espaces. | `public/js/brain.js` | `fix: refuse les messages vides et les espaces seuls` |
| ✖ accepte 250 caractères et refuse 251 (0.9851ms) | La limite utilisée dans le code était 280 au lieu de la constante `LIMITE` fixée à 250. | `public/js/brain.js` | `fix: utilise la limite de caractères configurée` |
| ✖ Contrat CP1 — validateMessage (14.2559ms) | Le contrat échouait à cause des erreurs de validation du message vide et de la limite de caractères. | `public/js/brain.js` | `fix: corrige la validation des messages` |
| ✖ ignore la casse et les espaces autour (4.9963ms) | `replyTo` mettait le message en minuscules mais ne supprimait pas les espaces autour. | `public/js/brain.js` | `fix: normalise les messages avant réponse` |
| ✖ reconnaît les deux mots du cahier personnel, quelles que soient la casse et les espaces autour (3.8492ms) | Les espaces autour du message empêchaient de reconnaître correctement les mots personnels. | `public/js/brain.js` | `fix: normalise les messages avant réponse` |
| ✖ répond à une phrase inconnue par un repli distinct (12.5294ms) | Une phrase inconnue renvoyait la même réponse que la commande `aide` au lieu d'une réponse distincte. | `public/js/brain.js` | `fix: ajoute un repli distinct pour les messages inconnus` |
| ✖ Contrat CP1 — replyTo (25.0694ms) | Le contrat échouait à cause de la normalisation des messages et du repli non distinct. | `public/js/brain.js` | `fix: corrige les réponses du cerveau` |
| ✖ view.js affiche du texte et ne décide pas des réponses (3.2217ms) | `view.js` utilisait `innerHTML` au lieu de `textContent` pour afficher les messages. | `public/js/view.js` | `fix: affiche les messages avec textContent` |
| ✖ Contrat CP1 — chaque module garde son rôle (47.4519ms) | Le module d'affichage utilisait `innerHTML`, ce qui ne respectait pas le contrat demandé. | `public/js/view.js` | `fix: affiche les messages avec textContent` |
| ✖ failing tests: | Plusieurs tests du contrat étaient encore rouges à cause des défauts listés ci-dessus. | `public/js/brain.js` et `public/js/view.js` | `fix: corrections du contrat CP1` |
| ✖ refuse le vide et les espaces seuls (2.6907ms) | Le code vérifiait le vide avant de retirer les espaces du message. | `public/js/brain.js` | `fix: refuse les messages vides et les espaces seuls` |
| ✖ accepte 250 caractères et refuse 251 (0.9851ms) | Le code utilisait 280 comme limite au lieu de `LIMITE` qui vaut 250. | `public/js/brain.js` | `fix: utilise la limite de caractères configurée` |
| ✖ ignore la casse et les espaces autour (4.9963ms) | Il manquait `trim()` avant de comparer le message. | `public/js/brain.js` | `fix: normalise les messages avant réponse` |
| ✖ reconnaît les deux mots du cahier personnel, quelles que soient la casse et les espaces autour (3.8492ms) | Les espaces autour empêchaient la correspondance avec les mots personnels. | `public/js/brain.js` | `fix: normalise les messages avant réponse` |
| ✖ répond à une phrase inconnue par un repli distinct (12.5294ms) | Le repli d'un message inconnu était identique à la réponse de `aide`. | `public/js/brain.js` | `fix: ajoute un repli distinct pour les messages inconnus` |
| ✖ view.js affiche du texte et ne décide pas des réponses (3.2217ms) | L'affichage utilisait `innerHTML` au lieu de `textContent`. | `public/js/view.js` | `fix: affiche les messages avec textContent` |

Avec l'agent : ce qu'il a proposé et que vous avez refusé, et pourquoi.

Pour aller plus loin : le nom renommé par votre commit `refactor:`, et pourquoi le nouveau est plus clair.

## R2 · Documenter le projet

Vos trois documents sont dans `atelier` : `README.md`, `SPEC.md` et `AGENTS.md`. Rien à recopier ici.

Pour aller plus loin, avec l'agent, les demandes du formateur :

| Demande | Ce qu'a fait l'agent | Votre décision | Règle d'`AGENTS.md` concernée (ou ajoutée) |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

## R3 · Premiers tests unitaires

| À remplir | Votre réponse |
|---|---|
| Fonction tirée | `estEnMajuscules(message)` |
| Le rouge vu (message exact) | `SyntaxError: The requested module '../public/js/brain.js' does not provide an export named 'estEnMajuscules'` |
| Identifiant du commit `test:` | `0612a3a` |
| Identifiant du commit `feat:` | `41af93c` |
| Casse volontaire : la ligne changée | `return message === message.toUpperCase();` remplacée temporairement par `return false;` |
| Casse volontaire : le test devenu rouge | `C1 : un message en majuscules donne true` et `C4 : il faut au moins deux lettres en majuscules` |
| Pour aller plus loin : la deuxième fonction | Pas encore fait |

### Critères C1 à C5

- **C1** : `'SALUT'` et `'OÙ EST LE REFUGE ?'` donnent `true`.
- **C2** : `'Salut'` et `'SALUT toi'` donnent `false`.
- **C3** : sans lettre (`'123 !'`), donne `false`.
- **C4** : il faut au moins deux lettres : `'OK'` donne `true`, `'A'` donne `false`.
- **C5** : une valeur qui n'est pas du texte donne `false`, sans erreur.

## R4 · La revue de code

| Patch | Accepté ou refusé | Fichier et ligne | Raison |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

Pour aller plus loin : le patch que vous avez corrigé, et ce que vous avez changé.

## Fin de journée

Chacun, une phrase : ce que vous savez faire ce soir et que vous ne saviez pas faire ce matin. Relisez votre positionnement : une notion est-elle passée de « à renforcer » à « à l'aise » ?



# Jour 3 · Terminer Cap Web

## Étape 1 · Le troisième mot

Prédiction : si nous ajoutons un troisième mot dans `MOTS`, la commande « aide » annoncera encore deux mots, car le nombre est écrit en dur dans la réponse.


## Étape 3 · Accessibilité avec Lighthouse

- Score avec le label : 100
- Score sans le label : 93
- Alerte Lighthouse : `Form elements do not have associated labels`













