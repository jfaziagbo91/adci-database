# Modèle Logique de Données (MLD) - ADCI V1

## Informations générales

| Élément | Valeur |
|----------|---------|
| Projet | ADCI |
| Version | V1.0 |
| Type | Modèle Logique de Données (MLD) |
| SGBD cible | PostgreSQL |
| Statut | En cours de conception |

---

# Objectif

Le Modèle Logique de Données (MLD) décrit l'organisation relationnelle des données de la plateforme ADCI.

Il constitue la référence technique avant la conception physique de la base PostgreSQL et permet de garantir la cohérence entre les besoins métier, le modèle UML et l'implémentation technique.

Le MLD sert de base à :

- la création du diagramme relationnel ;
- la conception du modèle PostgreSQL ;
- la génération des scripts SQL ;
- le développement des entités JPA/Hibernate ;
- la documentation technique du projet.

---

# Organisation du modèle

Le modèle est composé de quatre domaines fonctionnels.

## 1. Gestion des utilisateurs

- Utilisateur
- Authentification
- Role
- UtilisateurRole
- Profession

---

## 2. Gestion des adhésions

- DemandeAdhesion
- FormuleAdhesion
- StatutDemande
- HistoriqueStatut
- PieceJustificative
- TypePiece

---

## 3. Localisation

- Pays
- Region
- Departement
- Commune
- SectionLocale

---

## 4. Configuration

- Parametre

---

# Nombre de tables

| Domaine | Nombre |
|----------|--------:|
| Utilisateurs | 5 |
| Adhésions | 6 |
| Localisation | 5 |
| Configuration | 1 |
| **Total** | **17** |

---

# Liste des tables

| N° | Table |
|----|-------|
| 01 | Utilisateur |
| 02 | Authentification |
| 03 | Role |
| 04 | UtilisateurRole |
| 05 | Profession |
| 06 | DemandeAdhesion |
| 07 | FormuleAdhesion |
| 08 | StatutDemande |
| 09 | HistoriqueStatut |
| 10 | PieceJustificative |
| 11 | TypePiece |
| 12 | Pays |
| 13 | Region |
| 14 | Departement |
| 15 | Commune |
| 16 | SectionLocale |
| 17 | Parametre |

---

# Principes de conception

Le modèle relationnel respecte les principes suivants :

- normalisation des données ;
- séparation des données métier et des données techniques ;
- utilisation de clés primaires de type UUID ;
- intégrité référentielle assurée par des clés étrangères ;
- suppression des redondances ;
- évolutivité du modèle ;
- compatibilité avec PostgreSQL et Spring Boot.

---

# Conventions de nommage

- Nom des tables au singulier.
- Clés primaires nommées `id`.
- Clés étrangères suffixées par `_id`.
- Noms en `snake_case`.
- Types UUID pour les identifiants.
- Dates au format `TIMESTAMPTZ`.
- Contraintes et index nommés explicitement.

---

# Évolution du modèle

Chaque table est documentée dans un fichier dédié contenant :

- l'objectif métier ;
- le schéma relationnel ;
- les attributs ;
- les contraintes ;
- les index ;
- les relations ;
- les règles de gestion ;
- un exemple d'enregistrement.

Les évolutions du modèle seront tracées dans l'historique Git ainsi que dans le CHANGELOG du dépôt.