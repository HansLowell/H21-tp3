# Feature 9 - Affichage d'une review

## Description

En tant qu'acheteur, j'aimerais pouvoir accéder à une review d'un vendeur afin de l'examiner et déterminer s'il est digne de confiance ou non.

## Requête

`HTTP GET /seller/{sellerId}/reviews/{reviewId}`

## Réponse

`HTTP 200 OK`
```ts
{
  rating: number, // max 2 decimals, from 0 to 5
  comment: string
}
```

## Exceptions

| condition             | status | erreur             |
| --------------------- | ------ | ------------------ |
| `sellerId` inexistant | 404    | `SELLER_NOT_FOUND` |
| `reviewId` inexistant | 404    | `REVIEW_NOT_FOUND` |
