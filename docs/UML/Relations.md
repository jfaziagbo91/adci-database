# Relations entre les entités

## Objectif

Ce document décrit les relations existantes entre les entités du modèle UML de la plateforme ADCI.

Chaque relation est définie à partir des règles métier identifiées lors de la conception fonctionnelle.

---

# Gestion des utilisateurs

## Utilisateur ↔ Profession

Un utilisateur est associé à une profession.

Une profession peut être associée à plusieurs utilisateurs.

Justification :

La profession constitue un référentiel partagé.

---

## Utilisateur ↔ UtilisateurRole

Un utilisateur peut posséder plusieurs rôles.

Chaque association entre un utilisateur et un rôle est matérialisée par l'entité UtilisateurRole.

Justification :

Cette modélisation permet une gestion souple des habilitations.

---

## Role ↔ UtilisateurRole

Un rôle peut être attribué à plusieurs utilisateurs.

Chaque attribution est enregistrée dans UtilisateurRole.

---

# Gestion des adhésions

## Utilisateur ↔ DemandeAdhesion

Un utilisateur peut déposer plusieurs demandes d'adhésion au cours de sa vie.

Chaque demande appartient à un seul utilisateur.

---

## DemandeAdhesion ↔ FormuleAdhesion

Chaque demande est associée à une formule d'adhésion.

Une formule peut être utilisée par plusieurs demandes.

---

## DemandeAdhesion ↔ StatutDemande

Chaque demande possède un statut courant.

Un même statut peut être partagé par plusieurs demandes.

---

## DemandeAdhesion ↔ HistoriqueStatut

Chaque changement de statut est enregistré.

Une demande possède donc un historique complet.

---

## StatutDemande ↔ HistoriqueStatut

Chaque historique référence le statut appliqué.

Le même statut peut apparaître dans plusieurs historiques.

---

# Gestion documentaire

## DemandeAdhesion ↔ PieceJustificative

Une demande peut contenir plusieurs pièces justificatives.

Chaque pièce appartient à une seule demande.

---

## PieceJustificative ↔ TypePiece

Chaque pièce possède un type.

Un type peut être utilisé par plusieurs pièces.

---

# Localisation

## Pays ↔ Region

Un pays est composé de plusieurs régions.

Chaque région appartient à un seul pays.

---

## Region ↔ Departement

Une région contient plusieurs départements.

Chaque département appartient à une seule région.

---

## Departement ↔ Commune

Un département contient plusieurs communes.

Chaque commune appartient à un seul département.

---

## Commune ↔ SectionLocale

Une commune peut accueillir plusieurs sections locales.

Chaque section locale appartient à une seule commune.

---

# Organisation

## SectionLocale ↔ Utilisateur

Une section locale regroupe plusieurs utilisateurs.

Chaque utilisateur est rattaché à une seule section locale.

---

# Synthèse

Le modèle comporte :

- des relations de référence (Profession, StatutDemande, TypePiece) ;
- des relations organisationnelles (Pays, Région, Département, Commune, SectionLocale) ;
- des relations fonctionnelles (Utilisateur, DemandeAdhesion, PieceJustificative) ;
- une relation plusieurs-à-plusieurs entre Utilisateur et Role, implémentée par l'entité UtilisateurRole.

Cette organisation garantit un modèle normalisé, évolutif et conforme aux bonnes pratiques de conception UML.