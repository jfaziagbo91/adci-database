# Conventions de conception de la base de données ADCI

## Objectif

Ce document définit les conventions de conception de la base de données PostgreSQL du projet ADCI.

L'objectif est de garantir une base homogène, maintenable et facilement compréhensible.

---

# Convention de nommage

## Tables

- Nom au pluriel.
- Minuscules uniquement.
- Séparées par des underscores.

Exemples :

- adherents
- cotisations
- utilisateurs
- roles

---

## Colonnes

- Minuscules.
- Snake_case.
- Nom explicite.

Exemples :

- date_creation
- numero_telephone
- mot_de_passe
- date_naissance

---

## Clés primaires

Toutes les tables possèdent une clé primaire :

id

Type :

BIGSERIAL

---

## Clés étrangères

Nom de la clé :

<nom_table>_id

Exemples :

adherent_id

role_id

ville_id

---

## Dates

Toutes les tables possèdent :

created_at

updated_at

Le cas échéant :

deleted_at

pour la suppression logique.

---

## Booléens

Toujours préfixés par :

is_

ou

has_

Exemples :

is_active

is_verified

has_paid

---

## Contraintes

Toutes les contraintes sont nommées.

Exemple :

pk_adherents

fk_adherents_roles

uk_email

ck_statut

---

## Index

Les index portent le préfixe :

idx_

Exemple :

idx_email

idx_nom

---

## Séquences

Créées automatiquement par PostgreSQL.

---

## Normalisation

Objectif :

Troisième forme normale (3NF).

Toute duplication est évitée sauf justification métier.

---

## Intégrité référentielle

Toutes les relations utilisent des clés étrangères.

Les suppressions sont limitées afin d'éviter les pertes de données.

---

## Audit

Les informations suivantes seront historisées :

- création
- modification
- suppression logique
- utilisateur ayant effectué l'action

---

## Encodage

UTF-8

---

## Fuseau horaire

UTC

Affichage local géré par l'application.

---

## Versionnement

Toute modification de structure doit être réalisée via un script SQL versionné.

Aucune modification directe en production.

---

## Objectif final

Disposer d'une base :

- robuste ;
- évolutive ;
- documentée ;
- performante ;
- facilement maintenable.