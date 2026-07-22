# Table : Commune

## 1. Objectif

La table **Commune** référence les communes rattachées à un département.

Elle permet de localiser précisément les adhérents, les sections locales et les activités de l'association ADCI.

---

# 2. Description métier

Une commune appartient à un seul département.

Un département peut contenir plusieurs communes.

Une commune peut accueillir plusieurs sections locales.

Plusieurs utilisateurs peuvent être domiciliés dans une même commune.

Les coordonnées géographiques permettent de localiser la commune sur une carte et d'effectuer des recherches spatiales.

---

# 3. Schéma relationnel

COMMUNE

PK

- id

FK

- departement_id → Departement.id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| departement_id | UUID | Oui | Département de rattachement |
| code_administratif | VARCHAR(20) | Oui | Code administratif |
| nom | VARCHAR(150) | Oui | Nom de la commune |
| code_postal | VARCHAR(20) | Non | Code postal |
| population | INTEGER | Non | Population estimée |
| latitude | NUMERIC(10,7) | Non | Latitude GPS |
| longitude | NUMERIC(10,7) | Non | Longitude GPS |
| actif | BOOLEAN | Oui | Commune active |
| ordre_affichage | INTEGER | Non | Ordre d'affichage |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Date de modification |

---

# 5. Clé primaire

PK_COMMUNE

(id)

---

# 6. Clés étrangères

| Colonne | Référence |
|----------|-----------|
| departement_id | Departement(id) |

---

# 7. Contraintes

## PRIMARY KEY

PK_COMMUNE

## FOREIGN KEY

FK_COMMUNE_DEPARTEMENT

## UNIQUE

UQ_COMMUNE_DEPARTEMENT_CODE

UQ_COMMUNE_DEPARTEMENT_NOM

## CHECK

population >= 0

latitude BETWEEN -90 AND 90

longitude BETWEEN -180 AND 180

## NOT NULL

- departement_id
- code_administratif
- nom
- actif
- date_creation

---

# 8. Index

IDX_COMMUNE_DEPARTEMENT

IDX_COMMUNE_CODE

IDX_COMMUNE_NOM

IDX_COMMUNE_CODE_POSTAL

---

# 9. Relations

Departement

1 -------- N Commune

Commune

1 -------- N SectionLocale

Commune

1 -------- N Utilisateur

---

# 10. Règles de gestion

RG-COM-001

Chaque commune appartient à un seul département.

RG-COM-002

Un département peut contenir plusieurs communes.

RG-COM-003

Une commune peut accueillir plusieurs sections locales.

RG-COM-004

Plusieurs utilisateurs peuvent être domiciliés dans une même commune.

RG-COM-005

Le code administratif est unique dans un département.

RG-COM-006

Une commune inactive ne peut plus être sélectionnée.

RG-COM-007

La latitude doit être comprise entre -90 et +90.

RG-COM-008

La longitude doit être comprise entre -180 et +180.

RG-COM-009

Les coordonnées GPS sont facultatives en V1 mais recommandées.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| departement_id | UUID |
| code_administratif | 92046 |
| nom | Malakoff |
| code_postal | 92240 |
| population | 31000 |
| latitude | 48.8162000 |
| longitude | 2.2946000 |
| actif | TRUE |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table Commune |