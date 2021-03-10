# Feature 8 - Affichage d'un acheteur

## Description

En tant qu'acheteur, je peux accéder aux détails de mon compte afin d'y suivre mes offres.

## Requête

`GET /buyer/{buyerId}`

## Réponse

`HTTP 200 OK`

```ts
{
  id: string,
  name: string,
  biddingOffers: [
    {
      productId: string,
      amount: number, // arrondis MAX 2 decimals, montant de l'OFFRE et non du produit
      createdAt: datetime, // Date de création de l'OFFRE, pas du produit. ISO-8601 at UTC. exemple: "2020-01-01T00:00:00Z"
      biddingStatus: "ongoing" | "ended" // selon la date de fin de l'enchère sur le produit
    }
  ],
  obtainedProducts: [
    {
      productId: string,
      obtainedAt: datetime // ISO-8601 at UTC. exemple: "2020-01-01T00:00:00Z"
    }
  }
}
```

## Critères de succès

| critère | description                                                                                                               |
| ------- | ------------------------------------------------------------------------------------------------------------------------- |
| C1      | Toutes les offres valides effectuées par un acheteur sur un produit se retrouvent dans le champs `offers`.                |
| C2      | Le `biddingStatus` des offres sur les enchères de produit en court est `ongoing`.                                         |
| C3      | Une fois l'enchère d'un produit terminée, le `biddingStatus` des offres sur ce produit devient `ended`.                   |
| C4      | Lorsqu'une enchère se termine, une entrée correspondante à la dernière offre est créée dans le champs `obtainedProducts`. |
| C5      | Des tests E2E sur le contenu de `obtainedProducts` ne sont pas nécéssaires.                                               |

## Exceptions

| condition            | status | erreur            |
| -------------------- | ------ | ----------------- |
| `buyerId` inexistant | 404    | `BUYER_NOT_FOUND` |
