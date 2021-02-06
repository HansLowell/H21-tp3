# Feature 6 - Création d'un acheteur

## Description

En tant qu'utilisateur du service, j'aimerais pouvoir me créer un compte acheteur afin de placer des offres sur des produits.

## Requête

`HTTP POST /buyer`

```ts
{
  name: string,
  birthDate: datetime, // ISO-8601 at UTC
}
```

## Réponse

```
HTTP 201 CREATED
Headers:
  Location: string
```

... où le header `Location` contient l'URL vers le nouveau acheteur (`<host>/api/buyer/{buyerId}`)

## Exceptions

| condition            | status | erreur             |
| -------------------- | ------ | ------------------ |
| `birthDate` invalide | 400    | `INVALID_DATETIME` |
| champs vide          | 400    | `MISSING_FIELD`    |
