# Feature 2 - Affichage des produits (v2)

## Description

En temps qu'acheteur, je désire pouvoir visionner l'ensemble des produits à vendre.

## Requête

`HTTP GET /inventory`

### Query params

| nom            | type               | description                                                     |
| -------------- | ------------------ | --------------------------------------------------------------- |
| `status`       | `ongoing \| ended` | selon la date de fin                                            |
| `name`         | `string`           | **contient** le nom `name` (pas absolu, **pas** case sensitive) |
| `sellerId`     | `string`           | ID du seller                                                    |
| `minPrice`     | `number`           | prix min                                                        |
| `maxPrice`     | `number`           | prix max                                                        |
| `minInflation` | `number`           | % min de `currentPrice` / `initialPrice` (de 0 à 1)             |
| `maxInflation` | `number`           | % max de `currentPrice` / `initialPrice` (de 0 à 1)             |

## Réponse

`HTTP 200 OK`

```ts
{
  items: [
    {
      id: string,
      name: string,
      sellerId: string,
      description: string,
      initialPrice: number, // arrondi à 2 décimales
      currentPrice: number, // arrondi à 2 décimales
      startTime: datetime, // ISO-8601 at UTC
      endTime: datetime, // ISO-8601 at UTC
    },
  ];
}
```

## Exceptions

| condition               | status | erreur              |
| ----------------------- | ------ | ------------------- |
| `status` invalide       | 400    | `INVALID_STATUS`    |
| `sellerId` inexistant   | 404    | `SELLER_NOT_FOUND`  |
| `minPrice` invalide     | 400    | `INVALID_PRICE`     |
| `maxPrice` invalide     | 400    | `INVALID_PRICE`     |
| `minInflation` invalide | 400    | `INVALID_INFLATION` |
| `maxInflation` invalide | 400    | `INVALID_INFLATION` |
