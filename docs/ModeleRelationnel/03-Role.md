# Table : Role

## 1. Objectif

La table **Role** référence les différents rôles pouvant être attribués aux utilisateurs de la plateforme ADCI.

Elle permet de gérer les droits d'accès et les autorisations dans l'application.

---

# 2. Description métier

Un rôle définit un niveau de responsabilité et les fonctionnalités accessibles à un utilisateur.

Un utilisateur peut posséder plusieurs rôles.

Un rôle peut être attribué à plusieurs utilisateurs.

La relation est gérée par la table **UtilisateurRole**.

---

# 3. Schéma relationnel

ROLE

PK

- id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| code | VARCHAR(50) | Oui | Code unique du rôle |
| libelle | VARCHAR(100) | Oui | Nom du rôle |
| description | TEXT | Non | Description fonctionnelle |
| actif | BOOLEAN | Oui | Rôle actif |
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

PK_ROLE

## UNIQUE

UQ_ROLE_CODE

UQ_ROLE_LIBELLE

## NOT NULL

- code
- libelle
- actif
- date_creation

---

# 8. Index

IDX_ROLE_CODE

IDX_ROLE_LIBELLE

---

# 9. Relations

Role

1 -------- N UtilisateurRole

Utilisateur

N -------- N Role

(via UtilisateurRole)

---

# 10. Règles de gestion

RG-ROL-001

Le code d'un rôle est unique.

RG-ROL-002

Le libellé d'un rôle est unique.

RG-ROL-003

Un rôle peut être attribué à plusieurs utilisateurs.

RG-ROL-004

Un utilisateur peut posséder plusieurs rôles.

RG-ROL-005

Un rôle inactif ne peut plus être attribué à un utilisateur.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| code | ADMIN |
| libelle | Administrateur |
| description | Administration de la plateforme |
| actif | TRUE |

Autres exemples :

| Code | Libellé |
|------|----------|
| ADMIN | Administrateur |
| ADHERENT | Adhérent |
| RESPONSABLE_SECTION | Responsable de section |
| SECRETAIRE | Secrétaire |
| TRESORIER | Trésorier |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table Role |