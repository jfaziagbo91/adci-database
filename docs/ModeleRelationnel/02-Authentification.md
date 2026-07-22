# Table : Authentification

## 1. Objectif

La table **Authentification** stocke les informations nécessaires à la connexion des utilisateurs sur la plateforme ADCI.

Elle permet de gérer :

- l'authentification ;
- la sécurité des comptes ;
- la gestion des mots de passe ;
- le suivi des connexions ;
- le verrouillage des comptes.

---

# 2. Description métier

Chaque utilisateur possède un unique compte d'authentification.

Cette table est indépendante des informations métier afin de respecter le principe de séparation des responsabilités.

Elle est utilisée par Spring Security pour contrôler l'accès à l'application.

---

# 3. Schéma relationnel

AUTHENTIFICATION

PK

- id

FK

- utilisateur_id → Utilisateur.id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| utilisateur_id | UUID | Oui | Utilisateur associé |
| identifiant | VARCHAR(255) | Oui | Identifiant de connexion (email) |
| mot_de_passe_hash | VARCHAR(255) | Oui | Mot de passe chiffré (BCrypt) |
| derniere_connexion | TIMESTAMPTZ | Non | Dernière connexion |
| dernier_changement_mdp | TIMESTAMPTZ | Oui | Dernière modification du mot de passe |
| tentatives_echouees | INTEGER | Oui | Nombre de tentatives échouées |
| compte_verrouille | BOOLEAN | Oui | Indique si le compte est verrouillé |
| date_verrouillage | TIMESTAMPTZ | Non | Date du verrouillage |
| token_reinitialisation | VARCHAR(255) | Non | Jeton de réinitialisation |
| expiration_token | TIMESTAMPTZ | Non | Expiration du jeton |
| actif | BOOLEAN | Oui | Compte actif |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Dernière modification |

---

# 5. Clé primaire

| Nom | Type |
|------|------|
| id | UUID |

---

# 6. Clés étrangères

| Colonne | Référence |
|----------|-----------|
| utilisateur_id | Utilisateur(id) |

---

# 7. Contraintes

## PRIMARY KEY

PK_AUTHENTIFICATION

## FOREIGN KEY

FK_AUTHENTIFICATION_UTILISATEUR

## UNIQUE

UQ_AUTHENTIFICATION_UTILISATEUR

UQ_AUTHENTIFICATION_IDENTIFIANT

## CHECK

tentatives_echouees >= 0

---

# 8. Index

IDX_AUTH_IDENTIFIANT

IDX_AUTH_UTILISATEUR

IDX_AUTH_VERROUILLE

---

# 9. Relations

Utilisateur

1 -------- 1 Authentification

---

# 10. Règles de gestion

RG-AUT-001

Chaque utilisateur possède un seul compte d'authentification.

RG-AUT-002

L'identifiant de connexion est unique.

RG-AUT-003

Le mot de passe est stocké uniquement sous forme chiffrée (BCrypt).

RG-AUT-004

Après plusieurs tentatives de connexion échouées, le compte peut être verrouillé.

RG-AUT-005

Un jeton de réinitialisation possède une date d'expiration.

RG-AUT-006

La suppression d'un utilisateur entraîne la suppression de son authentification.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| utilisateur_id | UUID |
| identifiant | jean.aziagbo@email.fr |
| mot_de_passe_hash | $2a$10$... |
| tentatives_echouees | 0 |
| compte_verrouille | FALSE |
| actif | TRUE |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table Authentification |