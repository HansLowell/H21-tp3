# Feature 7 - Ajout d'une offre

## Description

En tant qu'acheteur, je peux faire une offre sur un produit.

## Critères de succès

| critère | description                                                    |
| ------- | -------------------------------------------------------------- |
| C1      | L'offre met à jour le `currentPrice` du produit                |
| C2      | L'offre apparait dans la liste d'offres `offers` de l'acheteur |
| C3      | Erreur si l'enchère est terminée                               |

## Requête

`POST /inventory/{productId}/offer`

```ts
{
  buyerId: string,
  amount: number
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
| enchère terminée                          | 400    | `BIDDING_ENDED`     |
| champs vide                               | 400    | `MISSING_FIELD`     |
