# Feature 5 - Affichage d'un vendeur (v2)

## Description

En tant qu'utilisateur du service, je désire visualiser les détails d'un vendeur.

## Requête

`GET /seller/{sellerId}`

## Réponse

`HTTP 200 OK`
```ts
{
  name: string,
  description: string,
  createdAt: datetime, // ISO-8601 at UTC
  rating: number // max 2 decimals, from 0 to 5
}
```

## Exceptions

| condition             | status | erreur             |
| --------------------- | ------ | ------------------ |
| `sellerId` inexistant | 404    | `SELLER_NOT_FOUND` |
