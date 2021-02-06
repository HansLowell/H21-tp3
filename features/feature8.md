# Feature 8 - Ajout d'une review

## Description

En tant qu'acheteur, j'aimerais pouvoir coter un vendeur afin de montrer s'il est digne de confiance ou non.

## Requête

`HTTP POST /seller/{sellerId}/review`

```ts
{
  buyerId: string,
  rating: number, // min 0, max 5, integer
  comment: string
}
```

## Réponse

```
HTTP 201 CREATED
Headers:
  Location: string
```

... où le header `Location` contient l'URL vers la review. (`<host>/api/seller/{sellerId}/review/{reviewId}`)

## Exceptions

| condition             | status | erreur             |
| --------------------- | ------ | ------------------ |
| `sellerId` inexistant | 404    | `SELLER_NOT_FOUND` |
| `buyerId` inexistant  | 404    | `BUYER_NOT_FOUND`  |
| `rating` invalide     | 400    | `INVALID_RATING`   |
| champs vide           | 400    | `MISSING_FIELD`    |
