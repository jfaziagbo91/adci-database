# Table : TypePiece

## 1. Objectif

La table **TypePiece** référence les différents types de pièces justificatives pouvant être demandées lors d'une adhésion.

Elle garantit la standardisation des documents attendus.

---

# 2. Description métier

Chaque pièce justificative appartient à un type.

Un type de pièce peut être utilisé par plusieurs pièces justificatives.

Cette table constitue un référentiel administrable.

---

# 3. Schéma relationnel

TYPE_PIECE

PK

- id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| code | VARCHAR(30) | Oui | Code unique |
| libelle | VARCHAR(100) | Oui | Nom du type |
| description | TEXT | Non | Description |
| obligatoire | BOOLEAN | Oui | Pièce obligatoire |
| extensions_autorisees | VARCHAR(255) | Oui | Extensions autorisées |
| taille_max_mo | INTEGER | Oui | Taille maximale en Mo |
| actif | BOOLEAN | Oui | Type actif |
| ordre_affichage | INTEGER | Non | Ordre d'affichage |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Date de modification |

---

# 5. Clé primaire

PK_TYPE_PIECE

(id)

---

# 6. Clés étrangères

Aucune.

---

# 7. Contraintes

PRIMARY KEY

PK_TYPE_PIECE

UNIQUE

UQ_TYPE_PIECE_CODE

UQ_TYPE_PIECE_LIBELLE

CHECK

taille_max_mo > 0

---

# 8. Index

IDX_TYPE_PIECE_CODE

IDX_TYPE_PIECE_LIBELLE

IDX_TYPE_PIECE_ACTIF

---

# 9. Relations

TypePiece

1 -------- N PieceJustificative

---

# 10. Règles de gestion

RG-TYP-001

Chaque type possède un code unique.

RG-TYP-002

Un type peut être utilisé par plusieurs pièces.

RG-TYP-003

Les extensions autorisées sont définies par l'administration.

RG-TYP-004

La taille maximale est exprimée en mégaoctets.

RG-TYP-005

Un type inactif ne peut plus être sélectionné.

---

# 11. Exemple d'enregistrement

| Code | Libellé | Obligatoire |
|------|----------|:-----------:|
| CNI | Carte Nationale d'Identité | Oui |
| PASSEPORT | Passeport | Oui |
| PHOTO | Photo d'identité | Oui |
| JUSTIF_DOMICILE | Justificatif de domicile | Non |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table TypePiece |