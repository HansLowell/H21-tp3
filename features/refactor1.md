# Refactor 1 - Création de Value Objects

## Description

En temps que gestionnaire de projet, je veux que certains types primitifs soient encapsulés dans des Value objects afin d'éviter une dette technique.

## Critères de succès

| critère | description                                               |
| ------- | --------------------------------------------------------- |
| C1      | L'ID des produits est encapsulé dans une ValueObject      |
| C2      | L'ID des vendeurs est encapsulé dans une ValueObject      |
| C3      | L'ID des acheteurs est encapsulé dans une ValueObject     |
| C4      | Les montant d'argent sont encapsulés dans une ValueObject |
| C5      | Des tests unitaires testent les Value Objects             |
