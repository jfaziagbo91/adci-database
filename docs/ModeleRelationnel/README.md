# Modèle Relationnel - ADCI

## Objectif

Ce dossier regroupe le Modèle Logique de Données (MLD) de la plateforme ADCI.

Le MLD décrit l'organisation des données de l'application avant leur implémentation dans PostgreSQL.

Il constitue la référence technique utilisée pour :

- concevoir la base de données PostgreSQL ;
- produire le diagramme relationnel ;
- générer les scripts SQL ;
- développer les entités JPA/Hibernate ;
- garantir la cohérence du modèle de données.

## Structure

Le dossier contient :

- un document de synthèse (`MLD-V1.md`) ;
- une fiche descriptive pour chaque table du modèle relationnel.

## Liste des tables

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

## Convention

Chaque fiche de table contient :

1. Objectif
2. Description métier
3. Schéma relationnel
4. Attributs
5. Clé primaire
6. Clés étrangères
7. Contraintes
8. Index
9. Relations
10. Règles de gestion
11. Exemple d'enregistrement
12. Historique