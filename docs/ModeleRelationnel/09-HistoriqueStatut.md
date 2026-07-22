# Table : HistoriqueStatut

## 1. Objectif

La table **HistoriqueStatut** enregistre l'ensemble des changements de statut d'une demande d'adhésion.

Elle garantit la traçabilité des traitements effectués tout au long du cycle de vie d'une demande.

---

# 2. Description métier

À chaque changement de statut d'une demande, un nouvel enregistrement est créé.

Cette table constitue un journal d'audit permettant de connaître :

- le statut précédent ;
- le nouveau statut ;
- la date du changement ;
- l'utilisateur ayant réalisé l'action ;
- le commentaire éventuel.

Une demande peut donc posséder plusieurs historiques.

---

# 3. Schéma relationnel

HISTORIQUE_STATUT

PK

- id

FK

- demande_adhesion_id → DemandeAdhesion.id
- statut_demande_id → StatutDemande.id
- utilisateur_id → Utilisateur.id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| demande_adhesion_id | UUID | Oui | Demande concernée |
| statut_demande_id | UUID | Oui | Nouveau statut |
| utilisateur_id | UUID | Oui | Utilisateur ayant effectué l'action |
| commentaire | TEXT | Non | Commentaire associé au changement |
| date_changement | TIMESTAMPTZ | Oui | Date et heure du changement |
| date_creation | TIMESTAMPTZ | Oui | Date de création technique |

---

# 5. Clé primaire

| Nom | Type |
|------|------|
| id | UUID |

---

# 6. Clés étrangères

| Colonne | Référence |
|----------|-----------|
| demande_adhesion_id | DemandeAdhesion(id) |
| statut_demande_id | StatutDemande(id) |
| utilisateur_id | Utilisateur(id) |

---

# 7. Contraintes

## PRIMARY KEY

PK_HISTORIQUE_STATUT

## FOREIGN KEY

FK_HISTORIQUE_DEMANDE

FK_HISTORIQUE_STATUT

FK_HISTORIQUE_UTILISATEUR

## NOT NULL

- demande_adhesion_id
- statut_demande_id
- utilisateur_id
- date_changement

---

# 8. Index

IDX_HISTORIQUE_DEMANDE

IDX_HISTORIQUE_STATUT

IDX_HISTORIQUE_UTILISATEUR

IDX_HISTORIQUE_DATE

---

# 9. Relations

DemandeAdhesion

1 -------- N HistoriqueStatut

StatutDemande

1 -------- N HistoriqueStatut

Utilisateur

1 -------- N HistoriqueStatut

---

# 10. Règles de gestion

RG-HIS-001

Chaque changement de statut crée un nouvel historique.

RG-HIS-002

Les historiques ne sont jamais modifiés.

RG-HIS-003

Les historiques ne sont jamais supprimés.

RG-HIS-004

Chaque historique est associé à un utilisateur.

RG-HIS-005

Une demande peut posséder un nombre illimité d'historiques.

RG-HIS-006

La date du changement correspond à la date effective de la transition.

---

# 11. Exemple d'enregistrement

| Champ | Valeur |
|--------|--------|
| id | UUID |
| demande_adhesion_id | UUID |
| statut_demande_id | UUID |
| utilisateur_id | UUID |
| commentaire | Dossier validé après contrôle |
| date_changement | 2026-07-22 14:35 |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table HistoriqueStatut |