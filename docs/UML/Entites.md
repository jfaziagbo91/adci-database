# Entités métier - Modèle UML

## Objectif

Ce document présente les entités métier composant le diagramme de classes UML de la plateforme ADCI.

Chaque entité est décrite selon sa responsabilité métier ainsi que ses principales relations avec les autres entités.

Le détail des attributs est documenté dans le dictionnaire de données.

---

# Vue d'ensemble

Le modèle UML de la V1 est composé de quinze entités réparties en cinq domaines fonctionnels.

| Domaine | Nombre d'entités |
|----------|------------------:|
| Gestion des utilisateurs | 4 |
| Gestion des adhésions | 4 |
| Gestion documentaire | 2 |
| Localisation | 4 |
| Organisation | 1 |

---

# Gestion des utilisateurs

## Utilisateur

### Description

Représente une personne disposant d'un compte sur la plateforme ADCI.

### Responsabilités

- S'authentifier.
- Gérer son profil.
- Déposer une demande d'adhésion.
- Consulter l'état de sa demande.
- Détenir un ou plusieurs rôles.

### Relations

- Profession
- SectionLocale
- UtilisateurRole
- DemandeAdhesion

---

## Role

### Description

Décrit les autorisations fonctionnelles accordées à un utilisateur.

### Responsabilités

- Définir les droits d'accès.
- Contrôler les permissions.

### Relations

- UtilisateurRole

---

## UtilisateurRole

### Description

Table d'association entre les utilisateurs et les rôles.

### Responsabilités

- Associer un ou plusieurs rôles à un utilisateur.
- Permettre une relation plusieurs-à-plusieurs.

### Relations

- Utilisateur
- Role

---

## Profession

### Description

Référentiel des professions.

### Responsabilités

- Classifier les utilisateurs selon leur activité professionnelle.

### Relations

- Utilisateur

---

# Gestion des adhésions

## DemandeAdhesion

### Description

Représente une demande d'adhésion déposée par un utilisateur.

### Responsabilités

- Enregistrer une demande.
- Suivre son état.
- Centraliser les pièces justificatives.

### Relations

- Utilisateur
- FormuleAdhesion
- StatutDemande
- HistoriqueStatut
- PieceJustificative

---

## FormuleAdhesion

### Description

Décrit une formule d'adhésion proposée par l'association.

### Responsabilités

- Définir les caractéristiques d'une adhésion.

### Relations

- DemandeAdhesion

---

## StatutDemande

### Description

Référentiel des états possibles d'une demande.

### Responsabilités

- Indiquer l'état courant d'une demande.

### Relations

- DemandeAdhesion
- HistoriqueStatut

---

## HistoriqueStatut

### Description

Conserve l'historique des changements de statut d'une demande.

### Responsabilités

- Garantir la traçabilité.
- Conserver les changements de statut.

### Relations

- DemandeAdhesion
- StatutDemande

---

# Gestion documentaire

## PieceJustificative

### Description

Représente un document déposé dans le cadre d'une demande d'adhésion.

### Responsabilités

- Stocker les documents.
- Associer les documents à une demande.

### Relations

- DemandeAdhesion
- TypePiece

---

## TypePiece

### Description

Référentiel des types de documents acceptés.

### Responsabilités

- Définir les catégories de pièces justificatives.

### Relations

- PieceJustificative

---

# Localisation

## Pays

### Description

Référentiel des pays.

### Relations

- Region

---

## Region

### Description

Subdivision administrative d'un pays.

### Relations

- Pays
- Departement

---

## Departement

### Description

Subdivision administrative d'une région.

### Relations

- Region
- Commune

---

## Commune

### Description

Commune de rattachement.

### Relations

- Departement
- SectionLocale

---

# Organisation

## SectionLocale

### Description

Représente une section locale du mouvement ADCI.

### Responsabilités

- Rattacher un utilisateur à une structure locale.

### Relations

- Commune
- Utilisateur

---

# Synthèse

Le modèle UML de la V1 est composé de quinze entités organisées autour de cinq domaines fonctionnels :

- Gestion des utilisateurs
- Gestion des adhésions
- Gestion documentaire
- Localisation
- Organisation

Ce découpage garantit une séparation claire des responsabilités et facilite les évolutions futures du système.