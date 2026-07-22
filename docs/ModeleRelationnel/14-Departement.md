# Table : Departement

## 1. Objectif

La table **Departement** référence les départements administratifs d'une région.

Elle constitue le deuxième niveau de la hiérarchie géographique de la plateforme ADCI.

---

# 2. Description métier

Un département appartient à une seule région.

Une région peut contenir plusieurs départements.

Un département peut contenir plusieurs communes.

---

# 3. Schéma relationnel

DEPARTEMENT

PK

- id

FK

- region_id → Region.id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| region_id | UUID | Oui | Région de rattachement |
| code_administratif | VARCHAR(20) | Oui | Code administratif |
| nom | VARCHAR(100) | Oui | Nom du département |
| chef_lieu | VARCHAR(100) | Non | Chef-lieu |
| actif | BOOLEAN | Oui | Département actif |
| ordre_affichage | INTEGER | Non | Ordre d'affichage |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Date de modification |

---

# 5. Clé primaire

PK_DEPARTEMENT

(id)

---

# 6. Clés étrangères

| Colonne | Référence |
|----------|-----------|
| region_id | Region(id) |

---

# 7. Contraintes

## PRIMARY KEY

PK_DEPARTEMENT

## FOREIGN KEY

FK_DEPARTEMENT_REGION

## UNIQUE

UQ_DEPARTEMENT_REGION_CODE

UQ_DEPARTEMENT_REGION_NOM

## NOT NULL

- region_id
- code_administratif
- nom
- actif

---

# 8. Index

IDX_DEPARTEMENT_REGION

IDX_DEPARTEMENT_CODE

IDX_DEPARTEMENT_NOM

---

# 9. Relations

Region

1 -------- N Departement

Departement

1 -------- N Commune

---

# 10. Règles de gestion

RG-DEP-001

Chaque département appartient à une seule région.

RG-DEP-002

Une région peut contenir plusieurs départements.

RG-DEP-003

Le code administratif est unique à l'intérieur d'une région.

RG-DEP-004

Deux régions différentes peuvent posséder un département portant le même nom.

RG-DEP-005

Un département inactif ne peut plus être sélectionné.

---

# 11. Exemple d'enregistrement

| Région | Code | Département | Chef-lieu |
|--------|------|-------------|------------|
| Abidjan | ABJ-01 | Abidjan Sud | Abidjan |
| Lagunes | LAG-02 | Dabou | Dabou |
| Île-de-France | 92 | Hauts-de-Seine | Nanterre |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table Departement |