# Modélisation UML

## Objectif

Cette documentation présente le modèle de classes UML de la base de données de la plateforme ADCI.

Le diagramme de classes UML constitue le modèle de référence de la conception de la base de données. Il décrit les entités métier, leurs attributs, leurs relations et leurs cardinalités avant leur implémentation dans PostgreSQL et Spring Boot.

---

# Choix de conception

Les décisions suivantes ont été retenues :

- UML est le langage de modélisation utilisé pour la conception.
- PostgreSQL est le système de gestion de base de données retenu.
- Les entités UML serviront de base à la création des entités JPA/Hibernate.
- Le modèle relationnel sera dérivé du diagramme de classes UML.
- Le schéma SQL sera construit à partir du modèle relationnel.

---

# Objectifs

Le diagramme UML permet de :

- représenter les entités métier ;
- définir les attributs de chaque entité ;
- modéliser les associations entre les entités ;
- préciser les cardinalités ;
- préparer la génération des entités JPA ;
- assurer la cohérence du modèle relationnel.

---

# Périmètre de la V1

La première version couvre les domaines suivants :

- Gestion des utilisateurs
- Gestion des rôles
- Gestion des adhésions
- Gestion documentaire
- Gestion de la localisation
- Gestion des sections locales

---

# Entités de la V1

Le modèle UML de la V1 est composé de quinze entités.

## Gestion des utilisateurs

- Utilisateur
- Role
- UtilisateurRole
- Profession

## Gestion des adhésions

- DemandeAdhesion
- FormuleAdhesion
- StatutDemande
- HistoriqueStatut

## Gestion documentaire

- PieceJustificative
- TypePiece

## Gestion de la localisation

- Pays
- Region
- Departement
- Commune
- SectionLocale

---

# Relations principales

Les principales relations sont les suivantes :

- Un utilisateur possède un ou plusieurs rôles.
- Un rôle peut être attribué à plusieurs utilisateurs.
- Un utilisateur peut déposer plusieurs demandes d'adhésion.
- Une demande d'adhésion est associée à une formule d'adhésion.
- Une demande possède un statut courant.
- Une demande possède un historique des changements de statut.
- Une demande peut contenir plusieurs pièces justificatives.
- Une pièce justificative est associée à un type de pièce.
- Une section locale appartient à une commune.
- Une commune appartient à un département.
- Un département appartient à une région.
- Une région appartient à un pays.

---

# Outils de modélisation

Les diagrammes UML sont réalisés avec Draw.io.

Les exports sont générés aux formats :

- Draw.io (.drawio)
- PNG
- SVG
- PDF

---

# Évolutions

Après validation du diagramme de classes UML, les étapes suivantes seront réalisées :

1. Définition des attributs.
2. Validation des cardinalités.
3. Construction du modèle relationnel.
4. Création du schéma PostgreSQL.
5. Implémentation des entités JPA/Hibernate.