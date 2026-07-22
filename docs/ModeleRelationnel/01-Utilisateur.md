# Table : Utilisateur

## 1. Objectif

La table **Utilisateur** stocke les informations relatives aux personnes utilisant la plateforme ADCI.

Elle constitue l'entité centrale du système et permet :

- d'identifier un utilisateur de manière unique ;
- de gérer les informations personnelles d'un adhérent ;
- d'associer une profession ;
- de rattacher un utilisateur à une section locale ;
- de gérer les demandes d'adhésion.

---

# 2. Description métier

Un utilisateur représente une personne physique utilisant la plateforme ADCI.

Selon son rôle, il peut être :

- Visiteur
- Adhérent
- Responsable de section
- Administrateur

Les rôles sont gérés dans la table **UtilisateurRole**.

Les informations d'authentification sont stockées dans la table **Authentification**.

---

# 3. Schéma relationnel

UTILISATEUR

PK
- id

FK
- profession_id → Profession.id
- section_locale_id → SectionLocale.id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| nom | VARCHAR(100) | Oui | Nom |
| prenom | VARCHAR(100) | Oui | Prénom |
| sexe | VARCHAR(20) | Oui | Sexe |
| date_naissance | DATE | Oui | Date de naissance |
| email | VARCHAR(255) | Oui | Adresse électronique |
| telephone | VARCHAR(30) | Oui | Téléphone |
| adresse | TEXT | Non | Adresse postale |
| profession_id | UUID | Oui | Profession |
| section_locale_id | UUID | Non | Section locale |
| actif | BOOLEAN | Oui | Compte actif |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Date de modification |
| cree_par | UUID | Non | Créateur |
| modifie_par | UUID | Non | Dernier modificateur |

---

# 5. Clé primaire

| Nom | Type |
|------|------|
| id | UUID |

---

# 6. Clés étrangères

| Colonne | Référence |
|----------|-----------|
| profession_id | Profession(id) |
| section_locale_id | SectionLocale(id) |
| cree_par | Utilisateur(id) |
| modifie_par | Utilisateur(id) |

---

# 7. Contraintes

## PRIMARY KEY

PK_UTILISATEUR

## FOREIGN KEY

FK_UTILISATEUR_PROFESSION

FK_UTILISATEUR_SECTION

FK_UTILISATEUR_CREATEUR

FK_UTILISATEUR_MODIFICATEUR

## UNIQUE

UQ_UTILISATEUR_EMAIL

## NOT NULL

- nom
- prenom
- sexe
- date_naissance
- email
- telephone
- profession_id
- actif
- date_creation

---

# 8. Index

IDX_UTILISATEUR_EMAIL

IDX_UTILISATEUR_NOM

IDX_UTILISATEUR_PROFESSION

IDX_UTILISATEUR_SECTION

---

# 9. Relations

Profession

1 ---- N Utilisateur

SectionLocale

1 ---- N Utilisateur

Utilisateur

1 ---- N DemandeAdhesion

Utilisateur

N ---- N Role

(via UtilisateurRole)

Utilisateur

1 ---- 1 Authentification

---

# 10. Règles de gestion

RG-UTI-001

L'adresse email doit être unique.

RG-UTI-002

Un utilisateur possède une seule profession.

RG-UTI-003

Une section locale est optionnelle.

RG-UTI-004

Un utilisateur peut posséder plusieurs rôles.

RG-UTI-005

Un utilisateur possède un seul compte d'authentification.

RG-UTI-006

Un utilisateur peut déposer plusieurs demandes d'adhésion au cours de sa vie.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| nom | AZIAGBO |
| prenom | Jean-François |
| email | jean.aziagbo@email.fr |
| telephone | +33612345678 |
| profession_id | UUID |
| section_locale_id | UUID |
| actif | TRUE |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table Utilisateur |