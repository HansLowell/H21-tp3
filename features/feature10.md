# Feature 10 - Ajout d'une offre

## Description

En tant qu'utilisateur du service, je désire erffectuer une offre sur un produit dans le but d'avoir une chance de l'obtenir.

## Requête

`POST /inventory/{productId}/offer`

```ts
{
  buyerId: string,
  amount: number // arrondi à 2 décimales
}
```

## Réponse

`HTTP 201 CREATED`

## Exceptions

| condition                                 | status | erreur              |
| ----------------------------------------- | ------ | ------------------- |
| `productId` inexistant                    | 404    | `PRODUCT_NOT_FOUND` |
| `buyerId` inexistant                      | 404    | `BUYER_NOT_FOUND`   |
| `amount` format invalide, pas assez élevé | 400    | `INVALID_AMOUNT`    |
| enchère terminée                          | 400    | `BIDDING_CLOSED`    |
| champs vide                               | 400    | `MISSING_FIELD`     |
