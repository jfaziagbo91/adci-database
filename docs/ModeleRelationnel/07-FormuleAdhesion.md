# Table : FormuleAdhesion

## 1. Objectif

La table **FormuleAdhesion** référence les différentes formules d'adhésion proposées par ADCI.

Elle permet de centraliser les caractéristiques de chaque formule afin d'éviter toute duplication des informations dans les demandes d'adhésion.

---

# 2. Description métier

Une formule d'adhésion définit les conditions d'adhésion proposées par l'association.

Chaque demande d'adhésion est obligatoirement associée à une seule formule.

Une même formule peut être utilisée par plusieurs demandes.

---

# 3. Schéma relationnel

FORMULE_ADHESION

PK

- id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| code | VARCHAR(30) | Oui | Code unique de la formule |
| libelle | VARCHAR(100) | Oui | Nom de la formule |
| description | TEXT | Non | Description détaillée |
| montant | NUMERIC(10,2) | Oui | Montant de la cotisation |
| devise | VARCHAR(3) | Oui | Devise (EUR, XOF...) |
| duree_mois | INTEGER | Oui | Durée de validité en mois |
| actif | BOOLEAN | Oui | Formule active |
| ordre_affichage | INTEGER | Non | Ordre d'affichage |
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

PK_FORMULE_ADHESION

## UNIQUE

UQ_FORMULE_CODE

UQ_FORMULE_LIBELLE

## CHECK

montant >= 0

duree_mois > 0

## NOT NULL

- code
- libelle
- montant
- devise
- duree_mois
- actif
- date_creation

---

# 8. Index

IDX_FORMULE_CODE

IDX_FORMULE_LIBELLE

IDX_FORMULE_ACTIF

---

# 9. Relations

FormuleAdhesion

1 -------- N DemandeAdhesion

---

# 10. Règles de gestion

RG-FOR-001

Chaque formule possède un code unique.

RG-FOR-002

Une formule peut être utilisée par plusieurs demandes d'adhésion.

RG-FOR-003

Une formule inactive ne peut plus être sélectionnée lors d'une nouvelle adhésion.

RG-FOR-004

Le montant de la cotisation ne peut pas être négatif.

RG-FOR-005

La durée de validité est exprimée en mois.

RG-FOR-006

La suppression physique d'une formule déjà utilisée est interdite.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| code | ADH_STANDARD |
| libelle | Adhésion Standard |
| montant | 20.00 |
| devise | EUR |
| duree_mois | 12 |
| actif | TRUE |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table FormuleAdhesion |