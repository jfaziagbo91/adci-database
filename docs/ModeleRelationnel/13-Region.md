# Table : Region

## 1. Objectif

La table **Region** référence les subdivisions administratives de premier niveau des pays.

Elle permet de structurer les données géographiques de manière hiérarchique.

---

# 2. Description métier

Une région appartient à un seul pays.

Un pays peut posséder plusieurs régions.

Une région peut contenir plusieurs départements.

---

# 3. Schéma relationnel

REGION

PK

- id

FK

- pays_id → Pays.id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| pays_id | UUID | Oui | Pays de rattachement |
| code | VARCHAR(20) | Oui | Code administratif |
| nom | VARCHAR(100) | Oui | Nom de la région |
| chef_lieu | VARCHAR(100) | Non | Chef-lieu de la région |
| actif | BOOLEAN | Oui | Région active |
| ordre_affichage | INTEGER | Non | Ordre d'affichage |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Date de modification |

---

# 5. Clé primaire

PK_REGION

(id)

---

# 6. Clés étrangères

| Colonne | Référence |
|----------|-----------|
| pays_id | Pays(id) |

---

# 7. Contraintes

## PRIMARY KEY

PK_REGION

## FOREIGN KEY

FK_REGION_PAYS

## UNIQUE

UQ_REGION_PAYS_CODE

UQ_REGION_PAYS_NOM

## NOT NULL

- pays_id
- code
- nom
- actif

---

# 8. Index

IDX_REGION_PAYS

IDX_REGION_CODE

IDX_REGION_NOM

---

# 9. Relations

Pays

1 -------- N Region

Region

1 -------- N Departement

---

# 10. Règles de gestion

RG-REG-001

Chaque région appartient à un seul pays.

RG-REG-002

Un pays peut posséder plusieurs régions.

RG-REG-003

Le code est unique à l'intérieur d'un même pays.

RG-REG-004

Deux pays différents peuvent utiliser le même code régional.

RG-REG-005

Une région inactive ne peut plus être sélectionnée.

---

# 11. Exemple d'enregistrement

| Pays | Code | Région | Chef-lieu |
|------|------|---------|------------|
| Côte d'Ivoire | ABJ | Abidjan | Abidjan |
| Côte d'Ivoire | YAM | Yamoussoukro | Yamoussoukro |
| France | IDF | Île-de-France | Paris |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table Region |