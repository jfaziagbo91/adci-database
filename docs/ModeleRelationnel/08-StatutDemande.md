# Table : StatutDemande

## 1. Objectif

La table **StatutDemande** référence les différents statuts du cycle de vie d'une demande d'adhésion.

Elle permet d'assurer un suivi cohérent de l'évolution des demandes.

---

# 2. Description métier

Chaque demande d'adhésion possède un seul statut courant.

Le statut évolue au cours du traitement de la demande.

Chaque changement de statut est enregistré dans la table **HistoriqueStatut**.

---

# 3. Schéma relationnel

STATUT_DEMANDE

PK

- id

---

# 4. Attributs

| Attribut | Type PostgreSQL | Obligatoire | Description |
|-----------|-----------------|-------------|-------------|
| id | UUID | Oui | Identifiant unique |
| code | VARCHAR(30) | Oui | Code unique du statut |
| libelle | VARCHAR(100) | Oui | Libellé du statut |
| description | TEXT | Non | Description métier |
| ordre | INTEGER | Oui | Ordre du workflow |
| est_final | BOOLEAN | Oui | Indique si le statut est terminal |
| actif | BOOLEAN | Oui | Statut actif |
| date_creation | TIMESTAMPTZ | Oui | Date de création |
| date_modification | TIMESTAMPTZ | Oui | Date de modification |

---

# 5. Clé primaire

| Nom | Type |
|------|------|
| id | UUID |

---

# 6. Clés étrangères

Aucune.

---

# 7. Contraintes

## PRIMARY KEY

PK_STATUT_DEMANDE

## UNIQUE

UQ_STATUT_CODE

UQ_STATUT_LIBELLE

## CHECK

ordre > 0

## NOT NULL

- code
- libelle
- ordre
- est_final
- actif
- date_creation

---

# 8. Index

IDX_STATUT_CODE

IDX_STATUT_LIBELLE

IDX_STATUT_ORDRE

---

# 9. Relations

StatutDemande

1 -------- N DemandeAdhesion

StatutDemande

1 -------- N HistoriqueStatut

---

# 10. Règles de gestion

RG-STA-001

Chaque statut possède un code unique.

RG-STA-002

Une demande possède un seul statut courant.

RG-STA-003

Un statut peut être utilisé par plusieurs demandes.

RG-STA-004

Chaque changement de statut est historisé.

RG-STA-005

Un statut final ne permet plus de poursuivre le workflow.

RG-STA-006

Un statut inactif ne peut plus être utilisé.

---

# 11. Exemple d'enregistrement

| Code | Libellé | Ordre | Est final |
|------|----------|:-----:|:---------:|
| BROUILLON | Brouillon | 1 | Non |
| SOUMISE | Soumise | 2 | Non |
| EN_ETUDE | En étude | 3 | Non |
| PIECES_COMPLEMENTAIRES | Pièces complémentaires demandées | 4 | Non |
| VALIDEE | Validée | 5 | Oui |
| REJETEE | Rejetée | 6 | Oui |
| ANNULEE | Annulée | 7 | Oui |

---

# 12. Historique

| Version | Auteur | Description |
|----------|---------|-------------|
| V1.0 | Jean-François AZIAGBO | Création de la documentation de la table StatutDemande |