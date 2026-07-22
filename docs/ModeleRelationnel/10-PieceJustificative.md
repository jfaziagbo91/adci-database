# Table : PieceJustificative

## 1. Objectif

La table **PieceJustificative** référence l'ensemble des documents transmis lors d'une demande d'adhésion.

Elle permet de suivre les pièces fournies, leur état de validation et leur emplacement de stockage.

---

# 2. Description métier

Une demande d'adhésion peut nécessiter plusieurs pièces justificatives.

Chaque pièce :

- appartient à une seule demande ;
- possède un type de pièce ;
- peut être validée ou rejetée par un administrateur.

Les fichiers sont stockés sur le serveur ou dans un stockage objet. La base de données ne conserve que les informations descriptives.

---

# 3. Schéma relationnel

PIECE_JUSTIFICATIVE

PK

- id

FK

- demande_adhesion_id → DemandeAdhesion.id
- type_piece_id → TypePiece.id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| demande_adhesion_id | UUID | Oui | Demande concernée |
| type_piece_id | UUID | Oui | Type de document |
| nom_fichier | VARCHAR(255) | Oui | Nom du fichier |
| chemin_fichier | TEXT | Oui | Emplacement du fichier |
| type_mime | VARCHAR(100) | Oui | Type MIME |
| taille_octets | BIGINT | Oui | Taille du fichier |
| date_depot | TIMESTAMPTZ | Oui | Date de dépôt |
| valide | BOOLEAN | Oui | Pièce validée |
| commentaire_validation | TEXT | Non | Observation du validateur |
| date_validation | TIMESTAMPTZ | Non | Date de validation |
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
| demande_adhesion_id | DemandeAdhesion(id) |
| type_piece_id | TypePiece(id) |

---

# 7. Contraintes

## PRIMARY KEY

PK_PIECE_JUSTIFICATIVE

## FOREIGN KEY

FK_PJ_DEMANDE

FK_PJ_TYPE

## CHECK

taille_octets > 0

## NOT NULL

- demande_adhesion_id
- type_piece_id
- nom_fichier
- chemin_fichier
- type_mime
- taille_octets
- date_depot

---

# 8. Index

IDX_PJ_DEMANDE

IDX_PJ_TYPE

IDX_PJ_DATE

IDX_PJ_VALIDATION

---

# 9. Relations

DemandeAdhesion

1 -------- N PieceJustificative

TypePiece

1 -------- N PieceJustificative

---

# 10. Règles de gestion

RG-PJ-001

Une demande peut comporter plusieurs pièces justificatives.

RG-PJ-002

Chaque pièce appartient à une seule demande.

RG-PJ-003

Chaque pièce possède un type.

RG-PJ-004

Les fichiers ne sont pas stockés dans la base de données.

RG-PJ-005

Seules les métadonnées sont enregistrées.

RG-PJ-006

Une pièce peut être validée ou rejetée.

RG-PJ-007

Une pièce rejetée peut être remplacée par une nouvelle version.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| demande_adhesion_id | UUID |
| type_piece_id | UUID |
| nom_fichier | carte_identite.pdf |
| chemin_fichier | /uploads/2026/07/carte_identite.pdf |
| type_mime | application/pdf |
| taille_octets | 548236 |
| valide | TRUE |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table PieceJustificative |