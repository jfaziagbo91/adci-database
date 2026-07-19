# ADCI Database

## Présentation

Ce dépôt contient l'ensemble des ressources relatives à la conception, à la documentation, au développement et au versionnement de la base de données PostgreSQL du projet ADCI.

La base de données constitue la source de vérité de la plateforme. Elle centralise les informations relatives aux adhérents, aux responsables, aux cotisations, aux événements, aux campagnes et à l'ensemble des fonctionnalités métier.

---

## Objectifs

- Concevoir une base de données robuste.
- Garantir l'intégrité des données.
- Assurer la traçabilité des évolutions.
- Faciliter la maintenance.
- Préparer les futures API.
- Documenter chaque élément du modèle de données.

---

## Technologies

- PostgreSQL
- pgAdmin 4
- DBeaver
- Draw.io
- Git
- GitHub
- SQL

---

## Organisation du dépôt

```text
adci-database/
├── docs/
├── diagrams/
├── sql/
├── scripts/
├── exports/
└── templates/
```

---

## Cycle de conception

Vision Produit

↓

Backlog Produit

↓

User Stories

↓

Dictionnaire de données

↓

MCD

↓

MLD

↓

MPD

↓

Création SQL

↓

Tests

↓

API

---

## Auteur

Jean-François AZIAGBO
=======
# ADCI Database

## Présentation

Ce dépôt contient l'ensemble des ressources relatives à la conception, à la documentation, au développement et au versionnement de la base de données PostgreSQL du projet ADCI.

La base de données constitue la source de vérité de la plateforme. Elle centralise les informations relatives aux adhérents, aux responsables, aux cotisations, aux événements, aux campagnes et à l'ensemble des fonctionnalités métier.

---

## Objectifs

- Concevoir une base de données robuste.
- Garantir l'intégrité des données.
- Assurer la traçabilité des évolutions.
- Faciliter la maintenance.
- Préparer les futures API.
- Documenter chaque élément du modèle de données.

---

## Technologies

- PostgreSQL 18
- pgAdmin 4
- pgModeler
- Draw.io
- Git
- GitHub
- SQL

---

## Organisation du dépôt

```
adci-database/
│
├── docs/
├── diagrams/
├── sql/
├── scripts/
├── exports/
└── templates/
```

---

## Cycle de conception

Vision Produit

↓

Backlog Produit

↓

User Stories

↓

Dictionnaire de données

↓

MCD

↓

MLD

↓

MPD

↓

Création SQL

↓

Tests

↓

API

---

## Convention de versionnement

Chaque évolution de la base de données est versionnée via Git.

Les scripts SQL sont conservés dans le dossier `sql/`.

Les diagrammes sont conservés dans `diagrams/`.

La documentation est centralisée dans `docs/`.

---

## Auteur

Projet ADCI

Product Owner :
Jean-François AZIAGBO