# TP3 - Énoncé

:calendar: **À remettre pour le 2 avril 2021 à 22h**

## Objectifs

- Utiliser des outils de planification et de gestion efficacement et de façon organisée
- Écrire des stories afin d'énoncer des ajouts de features
- Ajouter des nouvelles fonctionnalités à partir de récits utilisateurs
- Configurer un déploiement continue de A à Z

## Partie 1 - Outils de planification (10%)

**Avant** d'entamer la programmation, nous vous demandons de lire attentivement les exigences du tp. Nous vous demandons ensuite de planifier vos tâches _de développement logiciel_ avec **Github**.

1. :scroll: **Créez un _milestone_** pour la remise du tp. Insérez une capture d'écran afin de montrer les informations du milestone ainsi que les issues qu'il contient. Assurez-vous que toutes les issues soient présentes.
2. :scroll: **Créez des _issues_** afin de suivre votre progrès et de vous séparer la tâche. :warning: **Attention** Ce n'est pas nécéssairement 1 issue pour 1 feature. Assurez-vous également d'y remplir l'ensemble des parties tel que vu en laboratoire (l'issue doit au moins être en cours). Insérez une capture d'écran par issue (MAX 3).
3. :scroll: **Créez des _PRs_** afin de suivre les changements effectués ou en attente. Assurez-vous également d'y remplir l'ensemble des parties tel que vu en laboratoire. Insérez une capture d'écran par PRs **une fois résolue** (MAX 3). Vous n'avez pas à _scroller_ afin de montrer le contenu des activités et commentaires.
4. :scroll: **Créez un _Github Project_** contenant vos issues. Insérez une capture d'écran montrant le tableau résultant. Elle peut être effectuée au début comme à la fin de votre progrès. Nous devons au moins y voir les colonnes ainsi que quelques issues. Une seule capture suffit (pas besoin de _scroller_).

## Partie 2 - Écriture de stories (10%)

:scroll: Écrivez, dans votre fichier `tp3.md`, **8** récits utilisateurs de features ou améliorations que vous aimeriez implémenter dans votre projet. Assurez-vous de respecter les critères suivants:

- Niveau de complexité adéquat (faisable tout en demandant un certain effort)
- Les critères INVEST
- Des critères/conditions de succès (tests)

Également, vous n'avez pas besoin de :

- Suivre le format des features dans les énoncés (ce ne sont pas des récits utilisateurs)
- D'indiquer un pointage
- D'implémenter ces features (réservé pour le TP4)

## Partie 3 - Code (40%)

Pour cette partie, vous devez développer les features et refactors demandés. Les formats de requêtes et réponses utilisent la notation typée de Typescript. **On s'attend à une réponse dans le format JSON pour l'ensemble des appels à l'API**. Des tests automatisés vérifieront les bons retours de votre API. Nous corrigerons également la **clarté** (clean code), le **contenu**, l'**organisation** et l'**uniformisation** du code.

De plus, vous devez implémenter les mêmes types de tests que pour le TP2 ainsi que respecter les retours d'exceptions demandés.

### Features et refactors

- [Refactor 1](./features/refactor1.md)
- [Refactor 2](./features/refactor2.md)
- [Feature 6](./features/feature6.md)
- [Feature 7](./features/feature7.md)
- [Feature 8](./features/feature8.md)
- [Feature 9](./features/feature9.md)

## Partie 4 - Déploiement (40%)

Votre application étant maintenant entièrement fonctionnelle, il est temps de la déployer sur les Internets! Par contre, plusieurs étapes préliminaires sont requises. Ne vous découragez pas si des bugs persistent, c'est une partie qui peut être difficile!

### 4.1 - Création d'un pipeline sur Heroku

Vous devez créer un pipeline de déploiement sur Heroku comprenant les 2 environnements suivants:

- `staging` : déployé de façon automatique par le CI
- `production` : déployé (promoted) manuellement par vous

Vous devrez donc créer 2 applications Heroku afin de pouvoir ensuite les associer à un environnement de pipeline. Les urls peuvent être générés aléatoirement (donc pas nécéssairement reliées au terme `e-baie` ou `glo2003`).

### 4.2 - Configuration Heroku

Avant de pouvoir déployer sur Heroku, quelques étapes de configuration sont nécessaires. Ces dernières sont bien décrites sur le [Heroku Dev Center](https://devcenter.heroku.com/articles/deploying-java).

### 4.3 - Déploiement automatisé sur Heroku

Votre application doit être déployée sur Heroku de façon automatique lorsque le code est intégré à la branche de base (`main`). Ainsi, vous devrez créer un nouveau workflow avec **au moins** les `jobs` suivantes:

1. `test` : exécute les tests de la même façon que dans votre premier workflow.
2. `deploy` : déploie l'application sur l'environnement `staging` de votre pipeline d'Heroku.
   - Doit être effectué seulement **après** la/les job(s) de **test**.
   - Doit effectuer un health check après le déploiement (doit échouer si `/health` ne retourne pas `200 OK`)
   - Doit rollback (retourner à la version antérieure) si le healthcheck échoue
   - Certains Github Actions permettent d'automatiser ces commandes

Vous devriez donc avoir les 2 `workflows` suivants:

1. `test`, `CI` ou `build` qui exécute les tests au `push` sur toutes les branches, excepté la branche `main`.
2. `deploy` qui exécute les tests, puis ensuite le déploiement au `push` sur la branche `main` seulement.

### 4.4 - Pour la correction

1. Assurez-vous de créer un fichier `config/heroku_urls.json` avec la structure suivantes (sans les chevrons):

   ```json
   {
     "staging": "<url vers l'app en staging>",
     "production": "<url vers l'app en production>"
   }
   ```

2. :scroll: Dans votre fichier `tp3.md`, insérez une capture d'écran de votre pipeline Heroku. Vous pouvez brouiller ou cacher les adresses courriels si vous voulez.
