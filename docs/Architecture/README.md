# Architecture de la base de données ADCI

## Objectif

Ce document décrit l'architecture générale de la base de données PostgreSQL du projet ADCI.

Il présente les principes de conception, les domaines fonctionnels couverts et les règles d'organisation du schéma relationnel.

---

## Principes de conception

La base de données est conçue selon les principes suivants :

- séparation claire des responsabilités ;
- normalisation des données ;
- limitation de la redondance ;
- intégrité référentielle ;
- évolutivité du modèle ;
- traçabilité des modifications ;
- performances des requêtes.

---

## Domaines fonctionnels

La base de données couvre notamment les domaines suivants :

- Gestion des adhérents
- Gestion des responsables
- Gestion des cotisations
- Gestion des paiements
- Gestion des événements
- Gestion des campagnes
- Gestion des actualités
- Gestion documentaire
- Gestion des rôles et permissions
- Journalisation (logs)
- Paramétrage de la plateforme

---

## Architecture logique

Le modèle de données sera construit selon la démarche suivante :

1. Dictionnaire de données
2. Modèle Conceptuel de Données (MCD)
3. Modèle Logique de Données (MLD)
4. Modèle Physique de Données (MPD)
5. Implémentation PostgreSQL
6. Jeux de données
7. Optimisation
8. Versionnement

---

## Technologies

- PostgreSQL
- SQL
- pgAdmin 4
- DBeaver
- Draw.io
- Git
- GitHub

---

## Évolution

Ce document sera mis à jour à chaque évolution majeure de l'architecture de la base de données.