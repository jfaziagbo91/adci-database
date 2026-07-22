# Table : StatutPiece

## 1. Objectif

La table **StatutPiece** référence les différents statuts pouvant être attribués à une pièce justificative.

Elle permet de suivre le traitement des documents déposés par les adhérents.

---

# 2. Description métier

Chaque pièce justificative possède un statut courant.

Le statut évolue au cours de la vérification effectuée par les responsables de l'association.

Une même valeur de statut peut être utilisée par plusieurs pièces justificatives.

---

# 3. Schéma relationnel

STATUT_PIECE

PK

- id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| code | VARCHAR(30) | Oui | Code unique |
| libelle | VARCHAR(100) | Oui | Libellé |
| description | TEXT | Non | Description métier |
| ordre | INTEGER | Oui | Ordre du workflow |
| est_final | BOOLEAN | Oui | Statut terminal |
| actif | BOOLEAN | Oui | Statut actif |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Dernière modification |

---

# 5. Clé primaire

PK_STATUT_PIECE

(id)

---

# 6. Clés étrangères

Aucune.

---

# 7. Contraintes

## PRIMARY KEY

PK_STATUT_PIECE

## UNIQUE

UQ_STATUT_PIECE_CODE

UQ_STATUT_PIECE_LIBELLE

## CHECK

ordre > 0

## NOT NULL

- code
- libelle
- ordre
- est_final
- actif
- date_creation

---

# 8. Index

IDX_STATUT_PIECE_CODE

IDX_STATUT_PIECE_LIBELLE

IDX_STATUT_PIECE_ORDRE

IDX_STATUT_PIECE_ACTIF

---

# 9. Relations

StatutPiece

1 -------- N PieceJustificative

---

# 10. Règles de gestion

RG-STP-001

Chaque statut possède un code unique.

RG-STP-002

Une pièce justificative possède un seul statut courant.

RG-STP-003

Un statut peut être partagé par plusieurs pièces.

RG-STP-004

Un statut final clôt le traitement de la pièce.

RG-STP-005

Un statut inactif ne peut plus être utilisé.

RG-STP-006

Les transitions doivent respecter le workflow métier.

---

# 11. Exemple d'enregistrement

| Code | Libellé | Ordre | Est final |
|------|----------|:-----:|:---------:|
| DEPOSEE | Déposée | 1 | Non |
| EN_VERIFICATION | En cours de vérification | 2 | Non |
| VALIDEE | Validée | 3 | Oui |
| REJETEE | Rejetée | 4 | Oui |
| EXPIREE | Expirée | 5 | Oui |
| REMPLACEE | Remplacée | 6 | Oui |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table StatutPiece |