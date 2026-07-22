# Table : Profession

## 1. Objectif

La table **Profession** référence les professions pouvant être associées aux utilisateurs de la plateforme ADCI.

Elle permet de normaliser les données relatives à l'activité professionnelle des adhérents.

---

# 2. Description métier

Chaque utilisateur est associé à une profession.

Une même profession peut être partagée par plusieurs utilisateurs.

Cette table constitue un référentiel métier administrable.

---

# 3. Schéma relationnel

PROFESSION

PK

- id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| code | VARCHAR(30) | Oui | Code unique de la profession |
| libelle | VARCHAR(100) | Oui | Libellé de la profession |
| description | TEXT | Non | Description |
| actif | BOOLEAN | Oui | Profession active |
| ordre_affichage | INTEGER | Non | Ordre d'affichage dans les listes |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Date de modification |

---

# 5. Clé primaire

| Nom | Type |
|------|------|
| id | UUID |

---

# 6. Clés étrangères

Aucune.

---

# 7. Contraintes

## PRIMARY KEY

PK_PROFESSION

## UNIQUE

UQ_PROFESSION_CODE

UQ_PROFESSION_LIBELLE

## NOT NULL

- code
- libelle
- actif
- date_creation

---

# 8. Index

IDX_PROFESSION_CODE

IDX_PROFESSION_LIBELLE

IDX_PROFESSION_ACTIF

---

# 9. Relations

Profession

1 -------- N Utilisateur

---

# 10. Règles de gestion

RG-PRO-001

Une profession peut être associée à plusieurs utilisateurs.

RG-PRO-002

Le code d'une profession est unique.

RG-PRO-003

Le libellé d'une profession est unique.

RG-PRO-004

Une profession inactive ne peut plus être sélectionnée lors d'une nouvelle adhésion.

RG-PRO-005

La suppression physique d'une profession utilisée par un utilisateur est interdite.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| code | INGENIEUR |
| libelle | Ingénieur |
| description | Profession d'ingénieur |
| actif | TRUE |
| ordre_affichage | 1 |

Autres exemples :

| Code | Libellé |
|------|----------|
| ETUDIANT | Étudiant |
| ENSEIGNANT | Enseignant |
| FONCTIONNAIRE | Fonctionnaire |
| ENTREPRENEUR | Entrepreneur |
| COMMERCANT | Commerçant |
| RETRAITE | Retraité |
| SANS_EMPLOI | Sans emploi |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table Profession |