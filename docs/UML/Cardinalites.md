# Cardinalités du modèle UML

## Objectif

Ce document décrit les cardinalités des relations entre les entités de la plateforme ADCI.

Les cardinalités sont définies à partir des règles métier de la version V1.

---

# Gestion des utilisateurs

## Utilisateur — Profession

Cardinalité

- Utilisateur → Profession : (1..1)
- Profession → Utilisateur : (0..*)

Justification

Chaque utilisateur possède une profession.

Une profession peut être utilisée par plusieurs utilisateurs.

---

## Utilisateur — UtilisateurRole

Cardinalité

- Utilisateur → UtilisateurRole : (1..*)
- UtilisateurRole → Utilisateur : (1..1)

Justification

Un utilisateur possède un ou plusieurs rôles.

Chaque association concerne un seul utilisateur.

---

## Role — UtilisateurRole

Cardinalité

- Role → UtilisateurRole : (0..*)
- UtilisateurRole → Role : (1..1)

Justification

Un rôle peut être attribué à plusieurs utilisateurs.

Chaque association correspond à un seul rôle.

---

# Gestion des adhésions

## Utilisateur — DemandeAdhesion

Cardinalité

- Utilisateur → DemandeAdhesion : (0..*)
- DemandeAdhesion → Utilisateur : (1..1)

Justification

Un utilisateur peut effectuer plusieurs demandes.

Chaque demande appartient à un seul utilisateur.

---

## DemandeAdhesion — FormuleAdhesion

Cardinalité

- DemandeAdhesion → FormuleAdhesion : (1..1)
- FormuleAdhesion → DemandeAdhesion : (0..*)

Justification

Chaque demande est associée à une formule.

Une formule peut être choisie par plusieurs utilisateurs.

---

## DemandeAdhesion — StatutDemande

Cardinalité

- DemandeAdhesion → StatutDemande : (1..1)
- StatutDemande → DemandeAdhesion : (0..*)

Justification

Une demande possède un statut courant.

Un statut est partagé par plusieurs demandes.

---

## DemandeAdhesion — HistoriqueStatut

Cardinalité

- DemandeAdhesion → HistoriqueStatut : (0..*)
- HistoriqueStatut → DemandeAdhesion : (1..1)

Justification

Chaque changement de statut est historisé.

---

## HistoriqueStatut — StatutDemande

Cardinalité

- HistoriqueStatut → StatutDemande : (1..1)
- StatutDemande → HistoriqueStatut : (0..*)

Justification

Chaque historique fait référence à un statut.

---

# Gestion documentaire

## DemandeAdhesion — PieceJustificative

Cardinalité

- DemandeAdhesion → PieceJustificative : (0..*)
- PieceJustificative → DemandeAdhesion : (1..1)

Justification

Une demande peut contenir plusieurs documents.

---

## PieceJustificative — TypePiece

Cardinalité

- PieceJustificative → TypePiece : (1..1)
- TypePiece → PieceJustificative : (0..*)

Justification

Chaque document appartient à une catégorie.

---

# Localisation

## Pays — Region

Cardinalité

- Pays → Region : (1..*)
- Region → Pays : (1..1)

---

## Region — Departement

Cardinalité

- Region → Departement : (1..*)
- Departement → Region : (1..1)

---

## Departement — Commune

Cardinalité

- Departement → Commune : (1..*)
- Commune → Departement : (1..1)

---

## Commune — SectionLocale

Cardinalité

- Commune → SectionLocale : (0..*)
- SectionLocale → Commune : (1..1)

---

# Organisation

## SectionLocale — Utilisateur

Cardinalité

- SectionLocale → Utilisateur : (0..*)
- Utilisateur → SectionLocale : (1..1)

Justification

Chaque utilisateur est rattaché à une section locale.

Une section locale regroupe plusieurs utilisateurs.

---

# Synthèse des relations

| Relation | Cardinalité |
|----------|-------------|
| Utilisateur — Profession | N → 1 |
| Utilisateur — UtilisateurRole | 1 → N |
| Role — UtilisateurRole | 1 → N |
| Utilisateur — DemandeAdhesion | 1 → N |
| DemandeAdhesion — FormuleAdhesion | N → 1 |
| DemandeAdhesion — StatutDemande | N → 1 |
| DemandeAdhesion — HistoriqueStatut | 1 → N |
| HistoriqueStatut — StatutDemande | N → 1 |
| DemandeAdhesion — PieceJustificative | 1 → N |
| PieceJustificative — TypePiece | N → 1 |
| Pays — Region | 1 → N |
| Region — Departement | 1 → N |
| Departement — Commune | 1 → N |
| Commune — SectionLocale | 1 → N |
| SectionLocale — Utilisateur | 1 → N |

---

# Validation

L'ensemble de ces cardinalités constitue la référence officielle pour la construction du diagramme de classes UML et du modèle relationnel de la base de données ADCI V1.