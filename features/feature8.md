# Feature 8 - Ajout d'une review

## Description

En tant qu'acheteur, j'aimerais pouvoir coter un vendeur afin de montrer s'il est digne de confiance ou non.

## Requête

`HTTP POST /seller/{id}/review`

```ts
{
  buyerId: string,
  rating: number, // min 0, max 5, integer
  comment: string // max 200 caractères
}
```

## Réponse

```
HTTP 201 CREATED
Headers:
  Location: string
```

... où le header `Location` contient l'URL vers le user (`http://localhost:8080/api/seller/{sellerId}/reviews/{reviewId}`)
