# TP ITIL 5 — Amélioration d'un service helpdesk interne

Analyse et amélioration d'un service helpdesk interne présentant trois
dysfonctionnements récurrents — lenteur de traitement, tickets perdus, rappels
multiples sur un même problème — par application du framework ITIL (Version 5).

## Structure du dépôt

| Fichier | Contenu |
|---|---|
| `p1-csi-register.md` | Diagnostic sur les quatre dimensions, CSI Register priorisé, principe directeur mobilisé |
| `p2-slm-events.md` | SLA et SLO du helpdesk, classification des cinq événements journalisés |
| `p3-change-kb.md` | RFC-2026-014, article de base de connaissance KB-2026-007, positionnement dans le Product and Service Lifecycle |
| `logs.txt` | Journal source utilisé en Partie 2 |
| `README.md` | Synthèse, demande de service traitée, analyse critique |

## Fil conducteur

Le cas est traité comme un dossier unique et non comme quatre exercices
indépendants. L'amélioration n° 1 du CSI Register — instauration d'un point
d'entrée unique avec attribution obligatoire — identifiée en Partie 1, devient la
RFC de la Partie 3, fonde l'article de base de connaissance, et donne lieu à la
demande de service traitée ci-dessous.

---

## Demande de service traitée (pratique Service Request Management)

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

**Description**

> Suite à la mise en œuvre de la RFC-2026-014, je suis intégré à la rotation du
> rôle de dispatcheur à compter du 12/10. Le profil dont je dispose actuellement
> ne permet pas de modifier le champ « technicien assigné » sur un ticket dont je
> ne suis pas le destinataire, ni de fixer la priorité à la qualification. Je
> sollicite l'attribution du profil « dispatcheur » créé dans le cadre du
> changement.

**Journal de résolution**

> 06/10 10:02 — Prise en charge. Vérification de l'inscription du demandeur au
> planning de rotation : confirmée pour la semaine du 12/10.
>
> 07/10 11:30 — Profil « dispatcheur » attribué. Droits accordés : modification
> du champ d'affectation sur l'ensemble du périmètre helpdesk, attribution et
> reclassement de priorité. Test de connexion effectué avec le demandeur.
>
> 07/10 16:45 — Clôture après confirmation du demandeur.

### Justification du classement en demande de service

Ce ticket relève de **Service Request Management**, et non d'**Incident
Management**. La distinction n'est pas formelle : elle détermine le traitement,
les délais applicables et les indicateurs sur lesquels le ticket est comptabilisé.

| Critère | Demande de service | Incident |
|---|---|---|
| Nature | Besoin nouveau, prévu | Interruption ou dégradation non prévue |
| Service concerné | Fonctionne normalement | Est dégradé |
| Traitement | Procédure connue, souvent pré-approuvée | Diagnostic puis rétablissement |
| Urgence | Planifiable | Subie |

Dans le cas présent, aucun service n'est interrompu. Le demandeur ne subit pas
une panne : il sollicite un droit dont il n'a jamais disposé, en vue d'une
échéance connue. La demande est planifiable, ce qui justifie à la fois le
classement en P3 et le traitement dans le délai de résolution de 5 jours ouvrés
défini en Partie 2 — délai effectivement respecté, la résolution étant intervenue
en un jour ouvré.

**Point de vigilance.** La confusion inverse est fréquente et coûteuse : traiter
une demande de service comme un incident sature les indicateurs d'incidents et
fausse l'analyse des causes récurrentes. C'est un risque direct dans un service
dépourvu d'étape de qualification à l'entrée — le dysfonctionnement même
identifié en Partie 1.

---

## Tableau récapitulatif — Parties et pratiques mobilisées

| Partie | Objet | Pratique(s) ITIL 5 mobilisée(s) | Modèles et outils |
|---|---|---|---|
| **1** | Diagnostic | Continual Improvement | Quatre dimensions du produit et du service, CSI Register, principes directeurs |
| **2** | Pilotage | Service Level Management, Event Management | Échelle de priorité, SLA / SLO, classification Informational / Warning / Exception |
| **3** | Changement | Change Enablement, Knowledge Management | RFC, analyse d'impact, plan de rollback, CAB, article KB, Product and Service Lifecycle |
| **4** | Clôture | Service Request Management | Distinction demande / incident, ITIL AI Capability Model (6C) |

Deux pratiques sont mobilisées de façon transverse sans faire l'objet d'un
livrable dédié : **Incident Management**, déclenchée par les deux événements
classés Exception en Partie 2, et **Problem Management**, évoquée en cas de
récurrence de l'instabilité réseau sur plusieurs ports.

---

## Principe directeur le plus structurant sur l'ensemble du cas

### Principe retenu : « Collaborer et promouvoir la visibilité »

Ce principe a été identifié dès la Partie 1 et s'est révélé structurant sur les
quatre parties. Les trois symptômes du contexte sont, ramenés à leur mécanisme,
trois défauts de visibilité : un ticket non attribué n'est visible de personne,
donc il se perd ; l'utilisateur ne voit pas l'avancement de sa demande, donc il
rappelle ; le technicien ne voit pas les résolutions passées, donc il
re-diagnostique et le traitement s'allonge.

### Exemple concret tiré du TP

L'illustration la plus nette se trouve dans la **relation entre la Partie 1 et la
Partie 2**.

Les SLA définis en Partie 2 — délai de première réponse, délai de résolution —
sont calculés automatiquement par l'outil de ticketing. Ils paraissent donc
objectifs. Ils ne le sont pas : ils ne portent que sur les demandes enregistrées.
Tant que des demandes circulent par téléphone ou de vive voix, **les indicateurs
mesurent un périmètre partiel et affichent une performance meilleure que la
réalité vécue par les utilisateurs**. Un service pourrait ainsi présenter des
SLA tenus à 95 % tout en recevant les trois plaintes du contexte initial, sans
que la contradiction soit détectable dans les chiffres.

C'est ce constat qui a conduit à placer l'amélioration n° 1 en priorité 1, à
faire d'elle la RFC de la Partie 3, et à mentionner explicitement en Partie 2 que
les SLA ne sont réellement opposables qu'après son déploiement. La priorisation
ne découle pas d'un calcul effort/impact — les améliorations 1 et 3 partagent le
même couple *moyen / fort* — mais du fait que **rendre le flux visible conditionne
toute mesure ultérieure**.

### Principes écartés et motifs

**« Optimiser et automatiser »** a été écarté en Partie 1 : il aurait conduit à
chercher d'emblée une solution d'outillage, alors qu'ITIL recommande de ne pas
automatiser un processus qui n'est pas d'abord défini et maîtrisé. Automatiser
l'affectation dans un service où une partie des demandes n'est pas enregistrée
fige le contournement au lieu de le corriger.

**« Progresser de manière itérative avec du feedback »** a joué un rôle réel mais
localisé : il est intervenu en Partie 3, porté par l'approbateur du CAB, sous la
forme d'un déploiement pilote sur deux services et d'un point de contrôle à J+15.
Il a structuré le *rythme* du changement, non l'analyse ni la priorisation
d'ensemble.

---

## Analyse critique — Apport du module AI Governance et du modèle 6C

### Rappel du modèle

Le module **ITIL AI Governance** est une extension d'ITIL 5. Il s'appuie
notamment sur l'**ITIL AI Capability Model**, dit modèle **6C**, qui classe ce
qu'un système d'IA *fait* selon six capacités :

| Capacité | Fonction | Illustration en contexte helpdesk |
|---|---|---|
| **Creation** | Produire du contenu, du code, de la documentation | Rédaction d'un brouillon d'article de base de connaissance |
| **Curation** | Améliorer la qualité et la pertinence de données existantes | Détection des tickets en doublon |
| **Clarification** | Aider à naviguer et comprendre un contenu complexe | Résumé d'un ticket long et confus |
| **Cognition** | Identifier des schémas et des signaux non évidents | Détection de tickets récurrents révélant une cause commune |
| **Communication** | Interfaces en langage naturel | Agent conversationnel de dépôt de demande |
| **Coordination** | Exécution et orchestration autonomes d'actions | Affectation automatique d'un ticket à un technicien |

Chaque capacité appelle un niveau de supervision distinct, proportionné à
l'impact de la décision sur le service et sur les utilisateurs.

### Position retenue : apport faible sur le cas traité, mais non nul

**Le module n'apporte rien aux trois améliorations retenues.** Aucune ne comporte
de composante d'intelligence artificielle : instaurer un point d'entrée unique,
conditionner une clôture à la confirmation de l'utilisateur, constituer une base
de connaissance sont des mesures d'organisation et de processus. Il n'existe
aucune décision automatisée, donc aucun objet à gouverner. Mobiliser le module ici
reviendrait à produire une conformité sans contenu.

**Il apporte en revanche un élément décisif à un arbitrage effectivement posé.**

### L'arbitrage concerné

La solution la plus immédiate au symptôme des tickets perdus n'est pas celle qui
a été retenue. Face à des tickets que personne ne s'attribue, la réponse
spontanée est **l'affectation automatique** — un système qui lit le ticket,
détermine le domaine concerné et l'assigne au technicien compétent. Cette
solution supprime le rôle de dispatcheur, ne coûte aucune charge humaine, et
traite le symptôme immédiatement.

Elle a été écartée au profit d'une mesure organisationnelle. Le modèle 6C fournit
l'argument qui justifie cet écartement, et cet argument ne figure pas dans le
reste du framework.

**L'affectation automatique relève de la capacité Coordination**, celle qui
exécute une action de façon autonome. C'est la capacité la plus exigeante du
modèle en matière de supervision, pour une raison directement applicable ici : un
ticket mal affecté par un système automatique **reproduit exactement le symptôme
que le changement visait à supprimer** — un ticket qui n'est traité par personne —
avec une aggravation, puisque aucune personne identifiée n'en est responsable.
Le rôle de dispatcheur tournant, lui, désigne un humain nommé, joignable et
redevable de la qualification.

Le contraste avec les autres capacités est instructif : une IA qui résumerait les
tickets longs relève de **Clarification** et n'engage rien — le technicien
conserve la décision et détecte immédiatement un résumé erroné. Une IA qui
détecterait les tickets récurrents pour alimenter la base de connaissance relève
de **Cognition** et reste sous contrôle humain, l'article étant validé avant
publication. Ces deux usages seraient acceptables dès aujourd'hui, sous
supervision légère.

### Portée et limite de cet apport

L'apport du modèle 6C tient donc en une distinction : **il ne suffit pas de
demander si l'on recourt à l'IA, il faut demander ce que l'IA décide**. Deux
usages de même maturité technique appellent des régimes de gouvernance opposés
selon qu'ils informent une décision humaine ou qu'ils décident à sa place.

Cette distinction rejoint et précise un principe déjà présent dans le socle
ITIL — ne pas automatiser un processus non maîtrisé. La valeur ajoutée du module
est de fournir une grille de classement opérationnelle là où le principe
directeur restait une formule générale.

**Limite à signaler honnêtement.** Sur un cas de cette taille, cette contribution
reste marginale : l'arbitrage aurait pu être conduit sans le modèle, par
application du seul principe « Optimiser et automatiser ». La valeur du module se
manifesterait sur un service où plusieurs usages d'IA coexistent et où la question
n'est plus s'il faut gouverner, mais avec quelle intensité gouverner chacun. Ce
n'est pas le cas de figure traité ici.

---

## Sources de vérification

Le modèle 6C étant récent — ITIL (Version 5) a été publié le 12 février 2026 — la
composition des six capacités a été vérifiée auprès de PeopleCert et de sources
secondaires concordantes.
