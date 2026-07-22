# Table : SectionLocale

## 1. Objectif

La table **SectionLocale** référence les différentes sections locales de l'association ADCI.

Elle permet d'organiser les adhérents selon leur implantation géographique et de gérer les structures locales du mouvement.

---

# 2. Description métier

Une section locale représente une implantation territoriale d'ADCI.

Elle est rattachée à une commune.

Une commune peut accueillir plusieurs sections locales.

Une section locale peut accueillir plusieurs adhérents.

Chaque section possède un responsable désigné.

---

# 3. Schéma relationnel

SECTION_LOCALE

PK

- id

FK

- commune_id → Commune.id
- responsable_id → Utilisateur.id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| commune_id | UUID | Oui | Commune de rattachement |
| responsable_id | UUID | Non | Responsable de la section |
| code | VARCHAR(30) | Oui | Code unique de la section |
| nom | VARCHAR(150) | Oui | Nom officiel |
| adresse | VARCHAR(255) | Non | Adresse physique |
| code_postal | VARCHAR(20) | Non | Code postal |
| telephone | VARCHAR(30) | Non | Téléphone |
| email | VARCHAR(255) | Non | Adresse e-mail |
| latitude | NUMERIC(10,7) | Non | Latitude GPS |
| longitude | NUMERIC(10,7) | Non | Longitude GPS |
| date_creation_section | DATE | Non | Date officielle de création |
| actif | BOOLEAN | Oui | Section active |
| date_creation | TIMESTAMPTZ | Oui | Date de création technique |
| date_modification | TIMESTAMPTZ | Oui | Date de modification |

---

# 5. Clé primaire

PK_SECTION_LOCALE

(id)

---

# 6. Clés étrangères

| Colonne | Référence |
|----------|-----------|
| commune_id | Commune(id) |
| responsable_id | Utilisateur(id) |

---

# 7. Contraintes

## PRIMARY KEY

PK_SECTION_LOCALE

## FOREIGN KEY

FK_SECTION_COMMUNE

FK_SECTION_RESPONSABLE

## UNIQUE

UQ_SECTION_CODE

UQ_SECTION_NOM

## CHECK

latitude BETWEEN -90 AND 90

longitude BETWEEN -180 AND 180

## NOT NULL

- commune_id
- code
- nom
- actif
- date_creation

---

# 8. Index

IDX_SECTION_COMMUNE

IDX_SECTION_RESPONSABLE

IDX_SECTION_CODE

IDX_SECTION_NOM

---

# 9. Relations

Commune

1 -------- N SectionLocale

Utilisateur

1 -------- N SectionLocale

SectionLocale

1 -------- N Utilisateur

---

# 10. Règles de gestion

RG-SEC-001

Chaque section locale appartient à une seule commune.

RG-SEC-002

Une commune peut accueillir plusieurs sections locales.

RG-SEC-003

Chaque section possède un code unique.

RG-SEC-004

Le responsable de la section est un utilisateur de la plateforme.

RG-SEC-005

Une section inactive ne peut plus recevoir de nouveaux adhérents.

RG-SEC-006

Les coordonnées GPS permettent la géolocalisation de la section.

RG-SEC-007

L'adresse électronique d'une section doit être unique.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| commune_id | UUID |
| responsable_id | UUID |
| code | SEC-MALAKOFF |
| nom | Section ADCI Malakoff |
| adresse | 8 Rue de la Tour |
| code_postal | 92240 |
| telephone | +33 1 00 00 00 00 |
| email | malakoff@adci.org |
| latitude | 48.8162000 |
| longitude | 2.2946000 |
| actif | TRUE |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table SectionLocale |