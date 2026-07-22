# Table : Pays

## 1. Objectif

La table **Pays** référence les pays utilisés par la plateforme ADCI.

Elle garantit l'uniformité des données géographiques et évite les saisies libres.

---

# 2. Description métier

Chaque utilisateur réside dans un pays.

Les pays constituent le premier niveau de la hiérarchie géographique.

Un pays peut contenir plusieurs régions.

---

# 3. Schéma relationnel

PAYS

PK

- id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| code_iso2 | CHAR(2) | Oui | Code ISO 3166-1 Alpha-2 |
| code_iso3 | CHAR(3) | Oui | Code ISO 3166-1 Alpha-3 |
| nom | VARCHAR(100) | Oui | Nom officiel |
| gentilé | VARCHAR(100) | Non | Nom des habitants |
| indicatif_telephonique | VARCHAR(10) | Non | Indicatif international |
| devise | VARCHAR(10) | Non | Devise principale |
| actif | BOOLEAN | Oui | Pays disponible |
| ordre_affichage | INTEGER | Non | Ordre d'affichage |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Date de modification |

---

# 5. Clé primaire

PK_PAYS

(id)

---

# 6. Clés étrangères

Aucune.

---

# 7. Contraintes

## PRIMARY KEY

PK_PAYS

## UNIQUE

UQ_PAYS_CODE_ISO2

UQ_PAYS_CODE_ISO3

UQ_PAYS_NOM

## NOT NULL

- code_iso2
- code_iso3
- nom
- actif

---

# 8. Index

IDX_PAYS_NOM

IDX_PAYS_CODE_ISO2

IDX_PAYS_CODE_ISO3

---

# 9. Relations

Pays

1 -------- N Region

Pays

1 -------- N Utilisateur

---

# 10. Règles de gestion

RG-PAY-001

Chaque pays possède un code ISO unique.

RG-PAY-002

Un pays peut contenir plusieurs régions.

RG-PAY-003

Un pays inactif ne peut plus être sélectionné.

RG-PAY-004

Les codes ISO suivent la norme ISO 3166.

---

# 11. Exemple d'enregistrement

| Code ISO2 | Code ISO3 | Nom |
|------------|------------|---------------------|
| FR | FRA | France |
| CI | CIV | Côte d'Ivoire |
| BE | BEL | Belgique |
| CA | CAN | Canada |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table Pays |