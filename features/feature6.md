# Feature 6 - Création d'un acheteur

## Description

En tant qu'utilisateur du service, je peux me créer un compte acheteur.

## Critères de succès

| critère | description                     |
| ------- | ------------------------------- |
| C1      | L'utilisateur doit avoir 18 ans |

## Requête

`HTTP POST /buyer`

```ts
{
  name: string,
  birthDate: datetime, // ISO-8601 DATE ONLY, ex: "1990-12-31"
}
```

## Réponse

```
HTTP 201 CREATED
Headers:
  Location: string
```

... où le header `Location` contient l'URL vers le nouvel acheteur (`<host>/api/buyer/{buyerId}`)

## Exceptions

| condition            | status | erreur          |
| -------------------- | ------ | --------------- |
| `birthDate` invalide | 400    | `INVALID_DATE`  |
| champs vide          | 400    | `MISSING_FIELD` |
