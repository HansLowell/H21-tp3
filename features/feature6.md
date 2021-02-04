# Feature 6 - Création d'un acheteur

## Description

En tant qu'utilisateur du service, j'aimerais pouvoir me créer un compte acheteur afin de placer des offres sur des produits.

## Requête

`HTTP POST /buyer`
```ts
{
  name: string, // max 30 caractères
  birthDate: datetime, // ISO-8601 at UTC
}
```

## Réponse

```
HTTP 201 CREATED
Headers:
  Location: string
```

... où le header `Location` contient l'URL vers le nouveau utilisateur (`http://localhost:8080/api/buyer/{buyerId}`)

## Exceptions

| condition            | status | erreur             |
| -------------------- | ------ | ------------------ |
| `name` trop long     | 400    | `TEXT_TOO_LONG`    |
| `birthDate` invalide | 400    | `INVALID_DATETIME` |
