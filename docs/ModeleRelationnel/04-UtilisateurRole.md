# Table : UtilisateurRole

## 1. Objectif

La table **UtilisateurRole** permet d'associer un ou plusieurs rôles à un utilisateur.

Elle implémente la relation plusieurs-à-plusieurs (Many-to-Many) entre les tables **Utilisateur** et **Role**.

---

# 2. Description métier

Un utilisateur peut exercer plusieurs responsabilités au sein de l'association.

Inversement, un même rôle peut être attribué à plusieurs utilisateurs.

Cette table constitue le lien entre les utilisateurs et leurs autorisations fonctionnelles.

---

# 3. Schéma relationnel

UTILISATEUR_ROLE

PK

- id

FK

- utilisateur_id → Utilisateur.id
- role_id → Role.id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| utilisateur_id | UUID | Oui | Utilisateur concerné |
| role_id | UUID | Oui | Rôle attribué |
| date_attribution | TIMESTAMPTZ | Oui | Date d'attribution |
| date_fin | TIMESTAMPTZ | Non | Date de fin d'attribution |
| actif | BOOLEAN | Oui | Attribution active |
| cree_par | UUID | Oui | Utilisateur ayant attribué le rôle |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Date de modification |

---

# 5. Clé primaire

| Nom | Type |
|------|------|
| id | UUID |

---

# 6. Clés étrangères

| Colonne | Référence |
|----------|-----------|
| utilisateur_id | Utilisateur(id) |
| role_id | Role(id) |
| cree_par | Utilisateur(id) |

---

# 7. Contraintes

## PRIMARY KEY

PK_UTILISATEUR_ROLE

## FOREIGN KEY

FK_UR_UTILISATEUR

FK_UR_ROLE

FK_UR_CREATEUR

## UNIQUE

UQ_UTILISATEUR_ROLE

(utilisateur_id, role_id)

## CHECK

date_fin IS NULL OR date_fin >= date_attribution

---

# 8. Index

IDX_UR_UTILISATEUR

IDX_UR_ROLE

IDX_UR_ACTIF

---

# 9. Relations

Utilisateur

1 -------- N UtilisateurRole

Role

1 -------- N UtilisateurRole

Utilisateur

N -------- N Role

(via UtilisateurRole)

---

# 10. Règles de gestion

RG-UR-001

Un utilisateur peut posséder plusieurs rôles.

RG-UR-002

Un rôle peut être attribué à plusieurs utilisateurs.

RG-UR-003

Une même combinaison (utilisateur, rôle) ne peut exister qu'une seule fois.

RG-UR-004

Un rôle peut être désactivé sans être supprimé.

RG-UR-005

Chaque attribution est historisée par sa date d'attribution.

RG-UR-006

Une date de fin ne peut être antérieure à la date d'attribution.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| utilisateur_id | UUID |
| role_id | UUID |
| date_attribution | 2026-07-22 10:15 |
| date_fin | NULL |
| actif | TRUE |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table UtilisateurRole |