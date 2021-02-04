# Feature 7 - Affichage d'un acheteur

## Description

En tant qu'utilisateur du service, j'aimerais pouvoir accéder aux détails d'un acheteur.

## Requête

`GET /buyer/{buyerId}`

## Réponse

`HTTP 200 OK`
```ts
{
  id: string,
  name: string,
  birthDate: datetime, // ISO-8601 at UTC
  offers: [
    {
      productId: string,
      amount: number // 2 decimals
    }
  ],
  productsObtained: [
    {
      productId: string,
      expirationDate: datetime, // 30 jours après le endTime du produit
      price: number // 2 decimals
    }
  ]
}
```

## Exceptions

| condition            | status | erreur            |
| -------------------- | ------ | ----------------- |
| `buyerId` inexistant | 404    | `BUYER_NOT_FOUND` |
