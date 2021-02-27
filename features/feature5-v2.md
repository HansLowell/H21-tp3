# Feature 5 - Affichage d'un vendeur (v2)

## Description

En tant qu'utilisateur du service, je désire visualiser les détails d'un vendeur.

## Requête

`GET /seller/{sellerId}`

## Réponse

`HTTP 200 OK`

```ts
{
  id: string,
  name: string,
  description: string,
  createdAt: datetime, // ISO-8601 at UTC. exemple: "2020-01-01T00:00:00Z"
  rating: number // arrondi à 2 décimales, moyenne des rating de reviews
}
```

## Exceptions

| condition             | status | erreur             |
| --------------------- | ------ | ------------------ |
| `sellerId` inexistant | 404    | `SELLER_NOT_FOUND` |
