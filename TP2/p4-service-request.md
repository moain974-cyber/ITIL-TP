# Partie 4 — Clôture (Service Request Management)

## Demande de service traitée

### Champs du ticket

| Champ | Valeur |
|---|---|
| **N° de ticket** | 2026-1047 |
| **Titre** | Demande d'habilitation « dispatcheur » sur l'outil de ticketing |
| **Type** | Demande de service |
| **Demandeur** | Technicien helpdesk intégré à la rotation de dispatch |
| **Service concerné** | Helpdesk interne |
| **Catégorie** | Gestion des accès applicatifs |
| **Priorité** | P3 — Normal |
| **Statut** | Clos |
| **Date d'ouverture** | 06/10/2026 09:14 |
| **Date de prise en charge** | 06/10/2026 10:02 |
| **Date de résolution** | 07/10/2026 11:30 |
| **Date de clôture** | 07/10/2026 16:45 |
| **Technicien affecté** | Administrateur de l'outil de ticketing |

### Description

> Suite à la mise en œuvre de la RFC-2026-014, je suis intégré à la rotation du
> rôle de dispatcheur à compter du 12/10. Le profil dont je dispose actuellement
> ne permet pas de modifier le champ « technicien assigné » sur un ticket dont je
> ne suis pas le destinataire, ni de fixer la priorité à la qualification. Je
> sollicite l'attribution du profil « dispatcheur » créé dans le cadre du
> changement.

### Journal de résolution

> **06/10 10:02** — Prise en charge. Vérification de l'inscription du demandeur au
> planning de rotation : confirmée pour la semaine du 12/10.
>
> **07/10 11:30** — Profil « dispatcheur » attribué. Droits accordés :
> modification du champ d'affectation sur l'ensemble du périmètre helpdesk,
> attribution et reclassement de priorité. Test de connexion effectué avec le
> demandeur.
>
> **07/10 16:45** — Clôture après confirmation du demandeur.

---

## Justification du classement en demande de service

Ce ticket relève de **Service Request Management**, et non d'**Incident
Management**. La distinction n'est pas formelle : elle détermine le traitement,
les délais applicables et les indicateurs sur lesquels le ticket est
comptabilisé.

| Critère | Demande de service | Incident |
|---|---|---|
| Nature | Besoin nouveau, prévu | Interruption ou dégradation non prévue |
| Service concerné | Fonctionne normalement | Est dégradé |
| Traitement | Procédure connue, souvent pré-approuvée | Diagnostic puis rétablissement |
| Urgence | Planifiable | Subie |

Dans le cas présent, aucun service n'est interrompu. Le demandeur ne subit pas une
panne : il sollicite un droit dont il n'a jamais disposé, en vue d'une échéance
connue. La demande est planifiable, ce qui justifie à la fois le classement en P3
et le traitement dans le délai de résolution de 5 jours ouvrés défini en Partie 2
— délai effectivement respecté, la résolution étant intervenue en un jour ouvré.

**Point de vigilance.** La confusion inverse est fréquente et coûteuse : traiter
une demande de service comme un incident sature les indicateurs d'incidents et
fausse l'analyse des causes récurrentes. C'est un risque direct dans un service
dépourvu d'étape de qualification à l'entrée — le dysfonctionnement même identifié
en Partie 1.

---

## Rattachement au fil conducteur

Cette demande de service n'est pas un cas isolé : elle découle directement de la
RFC-2026-014 rédigée en Partie 3. La création du rôle de dispatcheur tournant
implique que chaque technicien intégré à la rotation dispose des droits
correspondants dans l'outil.

Elle illustre un point souvent négligé de la pratique Change Enablement : un
changement organisationnel génère des demandes de service en cascade, qu'il faut
avoir anticipées. Si ces habilitations n'avaient pas été traitées avant le
12/10, le dispositif aurait été déployé sans que les personnes concernées puissent
l'appliquer — un échec de mise en œuvre attribuable à la conduite du changement,
non au changement lui-même.

La synthèse d'ensemble, le tableau récapitulatif des pratiques, le principe
directeur structurant et l'analyse critique du module AI Governance figurent dans
le fichier `README.md`.
