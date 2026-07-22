# Table : DemandeAdhesion

## 1. Objectif

La table **DemandeAdhesion** enregistre les demandes d'adhésion soumises par les utilisateurs de la plateforme ADCI.

Elle permet de suivre l'ensemble du cycle de vie d'une demande, depuis sa création jusqu'à sa validation, son refus ou son annulation.

---

# 2. Description métier

Une demande d'adhésion est créée lorsqu'un utilisateur complète le formulaire d'adhésion.

Chaque demande est :

- associée à un utilisateur ;
- liée à une formule d'adhésion ;
- possède un statut courant ;
- peut comporter plusieurs pièces justificatives ;
- conserve l'historique de ses changements de statut.

Un utilisateur peut déposer plusieurs demandes au cours de sa vie.

---

# 3. Schéma relationnel

DEMANDE_ADHESION

PK

- id

FK

- utilisateur_id → Utilisateur.id
- formule_adhesion_id → FormuleAdhesion.id
- statut_demande_id → StatutDemande.id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| numero_demande | VARCHAR(30) | Oui | Numéro unique de la demande |
| utilisateur_id | UUID | Oui | Utilisateur demandeur |
| formule_adhesion_id | UUID | Oui | Formule choisie |
| statut_demande_id | UUID | Oui | Statut actuel |
| date_demande | TIMESTAMPTZ | Oui | Date de création |
| commentaire | TEXT | Non | Commentaire du demandeur |
| date_validation | TIMESTAMPTZ | Non | Date de validation |
| date_rejet | TIMESTAMPTZ | Non | Date de rejet |
| motif_rejet | TEXT | Non | Motif du rejet |
| actif | BOOLEAN | Oui | Demande active |
| date_creation | TIMESTAMPTZ | Oui | Date de création technique |
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
| formule_adhesion_id | FormuleAdhesion(id) |
| statut_demande_id | StatutDemande(id) |

---

# 7. Contraintes

## PRIMARY KEY

PK_DEMANDE_ADHESION

## FOREIGN KEY

FK_DEMANDE_UTILISATEUR

FK_DEMANDE_FORMULE

FK_DEMANDE_STATUT

## UNIQUE

UQ_NUMERO_DEMANDE

## NOT NULL

- numero_demande
- utilisateur_id
- formule_adhesion_id
- statut_demande_id
- date_demande
- actif

---

# 8. Index

IDX_DEMANDE_NUMERO

IDX_DEMANDE_UTILISATEUR

IDX_DEMANDE_STATUT

IDX_DEMANDE_FORMULE

IDX_DEMANDE_DATE

---

# 9. Relations

Utilisateur

1 -------- N DemandeAdhesion

FormuleAdhesion

1 -------- N DemandeAdhesion

StatutDemande

1 -------- N DemandeAdhesion

DemandeAdhesion

1 -------- N HistoriqueStatut

DemandeAdhesion

1 -------- N PieceJustificative

---

# 10. Règles de gestion

RG-DEM-001

Chaque demande possède un numéro unique.

RG-DEM-002

Une demande appartient à un seul utilisateur.

RG-DEM-003

Une demande est associée à une seule formule d'adhésion.

RG-DEM-004

Une demande possède un seul statut courant.

RG-DEM-005

Chaque changement de statut est historisé.

RG-DEM-006

Une demande peut comporter plusieurs pièces justificatives.

RG-DEM-007

Une demande validée ne peut plus être modifiée.

RG-DEM-008

Le motif de rejet est obligatoire lorsqu'une demande est refusée.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| numero_demande | DEM-2026-000001 |
| utilisateur_id | UUID |
| formule_adhesion_id | UUID |
| statut_demande_id | UUID |
| date_demande | 2026-07-22 09:30 |
| actif | TRUE |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table DemandeAdhesion |