# Partie 3 — Traitement du changement (Change Enablement + Knowledge Management + Product and Service Lifecycle)

## RFC — Mise en place d'un point d'entrée unique avec attribution obligatoire

### Identification

| Champ | Valeur |
|---|---|
| **Référence** | RFC-2026-014 |
| **Objet** | Instauration d'un canal unique de dépôt des demandes et d'une affectation nominative obligatoire à la création du ticket |
| **Demandeur** | Responsable du helpdesk interne |
| **Date de soumission** | 15/09/2026 |
| **Amélioration CSI associée** | N° 1 du CSI Register (Partie 1), priorité 1 |
| **Type de changement** | **Normal** |
| **Fenêtre de déploiement souhaitée** | Semaine du 05/10/2026 |

### Description du changement

Le changement porte sur trois éléments indissociables :

1. **Canal unique.** L'outil de ticketing devient le seul point d'entrée
   recevable. Les demandes formulées par téléphone ou de vive voix ne sont plus
   traitées directement : le technicien sollicité crée le ticket devant
   l'utilisateur ou l'invite à le déposer, puis traite la demande depuis l'outil.

2. **Affectation obligatoire.** Aucun ticket ne peut rester au statut « nouveau »
   au-delà de 30 minutes ouvrées. Un champ « technicien assigné » devient
   obligatoire à la qualification.

3. **Rôle de dispatcheur tournant.** Un technicien est désigné chaque jour, par
   rotation, pour qualifier les tickets entrants (priorité selon l'échelle
   définie en Partie 2) et les affecter. Le rôle est assorti d'une réduction de
   charge sur les autres tickets ce jour-là.

### Justification du type de changement

Le changement est classé **Normal**, à l'exclusion des deux autres catégories.

**Ce n'est pas un changement standard.** Un changement standard est un modèle
pré-approuvé, déjà exécuté à plusieurs reprises, dont le risque est connu et
maîtrisé. Rien de tel ici : c'est une première mise en œuvre, sans modèle
existant, et son effet dépend de l'adhésion des équipes — un facteur qui ne peut
pas être pré-évalué.

**Ce n'est pas un changement urgent.** La procédure d'urgence est réservée aux
situations où l'absence de changement cause un préjudice immédiat, typiquement le
rétablissement d'un service interrompu. Le dysfonctionnement traité ici est
chronique, installé depuis longtemps, et n'appelle aucune accélération. Recourir
à la procédure d'urgence reviendrait à contourner l'évaluation par le CAB, alors
que c'est précisément l'évaluation qui manque à ce changement organisationnel.

**C'est donc un changement normal** : il nécessite une évaluation formelle
préalable, une planification et une approbation avant déploiement.

### Analyse d'impact

#### Populations affectées

| Population | Nature de l'impact | Intensité |
|---|---|---|
| Techniciens helpdesk | Nouvelle obligation de saisie, rotation sur le rôle de dispatcheur, perte de la possibilité de choisir ses tickets | **Forte** |
| Utilisateurs habitués au canal oral | Perte d'un canal informel perçu comme plus rapide, obligation de passer par l'outil | **Forte** |
| Utilisateurs déjà utilisateurs de l'outil | Aucun changement de pratique, bénéfice sur les délais | Faible |
| Responsable helpdesk | Nouvelle charge de suivi de la rotation et des tickets non affectés | Moyenne |

#### Risques de régression identifiés

**Risque 1 — Report de la charge sur le dispatcheur du jour.**
Le technicien affecté au rôle voit son temps de traitement amputé. Si la
réduction de charge compensatoire n'est pas effective, les tickets dont il a la
responsabilité par ailleurs accumulent du retard. La lenteur ne disparaît pas :
elle se déplace. *Probabilité : moyenne. Gravité : moyenne.*

**Risque 2 — Contournement du canal unique.**
C'est le risque principal. Les utilisateurs habitués à solliciter directement un
technicien connu peuvent continuer à le faire. Si les techniciens cèdent, le
service se retrouve avec deux flux au lieu d'un — une situation **plus dégradée
qu'avant le changement**, puisque les indicateurs afficheraient alors une
amélioration trompeuse tout en ignorant une part du volume réel.
*Probabilité : forte. Gravité : forte.*

**Risque 3 — Dégradation perçue pour les demandes très courtes.**
Une demande réglée en deux minutes à l'oral exige désormais une création de
ticket. Le coût administratif peut dépasser le coût de traitement, et nourrir un
rejet du dispositif. *Probabilité : forte. Gravité : faible.*

**Risque 4 — Qualification erronée par le dispatcheur.**
La priorité est attribuée par un technicien qui ne connaît pas nécessairement le
contexte métier du demandeur. Une demande critique classée P3 subirait un délai
contractuel de 5 jours. *Probabilité : moyenne. Gravité : forte.*

#### Mesures de réduction associées

- Risque 1 : réduction formalisée à 50 % de la charge de tickets du dispatcheur
  le jour de sa rotation, contrôlée hebdomadairement.
- Risque 2 : consigne écrite et communication préalable aux services ;
  affichage hebdomadaire du nombre de tickets créés par canal pendant le premier
  mois.
- Risque 3 : création d'un modèle de ticket simplifié à trois champs pour les
  demandes de moins de 5 minutes.
- Risque 4 : possibilité de reclassement de priorité par le technicien affecté
  dans les 2 heures suivant l'affectation, avec traçabilité du reclassement.

### Plan de rollback

Le retour arrière est possible à tout moment pendant les 4 semaines suivant le
déploiement. Il est déclenché si l'un des deux critères suivants est atteint :

- plus de 30 % des demandes continuent d'arriver hors de l'outil à la fin de la
  semaine 3 ;
- le délai moyen de première réponse se dégrade de plus de 20 % par rapport à la
  mesure de référence établie avant déploiement.

**Procédure de retour arrière**

| Étape | Action | Responsable | Délai |
|---|---|---|---|
| 1 | Décision formalisée de rollback, consignée dans le ticket de changement | Responsable helpdesk | J |
| 2 | Retrait du caractère obligatoire du champ « technicien assigné » dans le formulaire de l'outil | Administrateur de l'outil | J, sous 1 h |
| 3 | Suspension de la rotation de dispatcheur, information de l'équipe | Responsable helpdesk | J, sous 2 h |
| 4 | Réouverture officielle du canal téléphonique, communication aux services | Responsable helpdesk | J+1 |
| 5 | Conservation intégrale des tickets créés pendant la période d'essai | Administrateur de l'outil | — |

**Points déterminants de ce plan**

- Le rollback est un **retrait de contrainte**, pas une restauration de données.
  Aucune migration n'ayant lieu, il n'existe aucun risque de perte : les tickets
  créés pendant l'essai restent exploitables, et constituent d'ailleurs le
  matériau d'analyse de l'échec.
- La configuration antérieure du formulaire est exportée et archivée **avant**
  déploiement, ce qui permet une restauration à l'identique plutôt qu'une
  reconstruction de mémoire.
- Le rollback est déclenché sur **critère chiffré et daté**, non sur ressenti.
  C'est ce qui le distingue d'un abandon progressif du dispositif, l'issue la plus
  probable en l'absence de critère explicite.

### Simulation de validation par le CAB

**Position du demandeur — Responsable du helpdesk**

> Les trois plaintes remontées par les utilisateurs ont une racine commune : une
> partie du flux est invisible. Nous ne mesurons pas notre volume réel, donc nous
> ne pilotons rien. Ce changement n'ajoute aucune fonctionnalité et n'engage
> aucun coût d'acquisition : il rend visible un flux existant.
>
> Je souligne qu'il conditionne les deux autres améliorations inscrites au CSI
> Register. Constituer une base de connaissance sur un historique incomplet nous
> ferait documenter les sujets les mieux tracés, pas les plus fréquents. Reporter
> ce changement, c'est reporter tout le programme d'amélioration.
>
> Sur le risque de contournement, que je reconnais comme le plus sérieux : il est
> mesurable dès la première semaine et j'ai fixé un seuil de rollback à 30 %. Le
> dispositif est réversible en moins de deux heures.

**Position de l'approbateur — Représentant des services utilisateurs au CAB**

> Je ne conteste pas le diagnostic, je conteste la séquence.
>
> Le changement supprime un canal aujourd'hui utilisé avant d'avoir démontré que
> le canal de remplacement tient la charge. Si le dispositif de dispatch
> s'engorge en semaine 1, les utilisateurs perdent leur solution de repli et le
> service se dégrade réellement, pas seulement dans les indicateurs. Vos
> utilisateurs subiront un préjudice pour un bénéfice qui, lui, est différé.
>
> Deuxième réserve : l'attribution de priorité par un dispatcheur qui ne connaît
> pas le métier du demandeur. Une demande bloquante classée P3 se voit opposer un
> délai de 5 jours ouvrés. Votre mesure de réduction existe, mais elle repose sur
> la vigilance du technicien affecté, pas sur une garantie.
>
> Je ne rejette pas la RFC. Je conditionne mon approbation à trois exigences :
>
> 1. **Déploiement progressif** sur deux services pilotes pendant deux semaines
>    avant généralisation, plutôt qu'une bascule simultanée.
> 2. **Mesure de référence établie avant déploiement** — délai moyen de première
>    réponse et volume hebdomadaire — sans quoi aucun critère de rollback n'est
>    évaluable.
> 3. **Point de contrôle formel à J+15**, avec décision explicite de poursuite ou
>    de rollback, et non simple reconduction tacite.

**Décision du CAB**

RFC **approuvée sous conditions**, les trois exigences de l'approbateur étant
intégrées au plan de déploiement. Nouvelle fenêtre : pilote à compter du
05/10/2026, généralisation conditionnée au point de contrôle du 20/10/2026.

*Observation : l'exigence de déploiement progressif formulée par le CAB
correspond au principe directeur « Progresser de manière itérative avec du
feedback ». Le débat n'a pas porté sur la pertinence du changement, sur laquelle
les deux parties s'accordent, mais sur son rythme — ce qui est la fonction
propre d'un CAB.*

---

## Article de base de connaissance (pratique Knowledge Management)

> **Référence** : KB-2026-007
> **Créé le** : 20/10/2026
> **Public** : techniciens helpdesk
> **Statut** : validé

### Symptôme

Un utilisateur signale qu'une demande formulée auprès du helpdesk est restée sans
suite. Aucun ticket correspondant n'est retrouvé dans l'outil lors d'une
recherche par nom de demandeur ou par mot-clé.

Le signalement prend généralement l'une de ces trois formes :

- « j'avais appelé la semaine dernière et je n'ai jamais eu de retour » ;
- l'utilisateur dépose un nouveau ticket pour un problème qu'il déclare avoir
  déjà signalé ;
- l'utilisateur cite le nom d'un technicien à qui il a parlé directement.

### Cause

La demande n'a jamais été enregistrée dans l'outil de ticketing. Elle a été
formulée par un canal non tracé — appel direct sur la ligne d'un technicien,
sollicitation dans un couloir, message adressé en personne — et n'a pas fait
l'objet d'une création de ticket.

Le problème n'est pas une perte de données dans l'outil : c'est une demande qui
n'y est jamais entrée. Aucune recherche, aussi complète soit-elle, ne peut donc
la retrouver.

**Cause secondaire à écarter avant conclusion.** Le ticket peut exister mais être
invisible dans la vue courante s'il a été clôturé prématurément par un autre
technicien. Vérifier systématiquement en incluant les tickets clos avant de
conclure à une absence d'enregistrement.

### Résolution

1. **Rechercher en incluant les tickets clos.** Filtrer sur le demandeur, tous
   statuts confondus, sur les 60 derniers jours. Si un ticket clos correspond au
   sujet, il s'agit d'une clôture prématurée : le rouvrir plutôt que d'en créer
   un nouveau, afin de conserver l'historique de traitement.

2. **Si aucun ticket n'existe, en créer un immédiatement**, pendant l'échange
   avec l'utilisateur. Renseigner en commentaire la date approximative de la
   demande initiale telle que l'utilisateur l'indique. Cette information est
   nécessaire au suivi du taux de contournement du canal unique.

3. **Qualifier la priorité selon l'échelle en vigueur.** L'ancienneté de la
   demande ne modifie pas sa priorité : un sujet non bloquant reste P3, même
   signalé depuis trois semaines.

4. **Informer l'utilisateur de la procédure applicable** : toute demande doit
   être déposée via le portail, ou faire l'objet d'une création de ticket
   immédiate si elle est formulée oralement. Préciser qu'il recevra désormais un
   retour nominatif sous le délai correspondant à sa priorité.

5. **Ne pas traiter la demande hors outil, même si elle est courte.** C'est
   précisément ce réflexe qui reproduit la situation décrite dans cet article.
   Pour les demandes de moins de cinq minutes, utiliser le modèle de ticket
   simplifié à trois champs.

### Mots-clés

`ticket perdu` · `demande sans suite` · `sans trace` · `demande orale` ·
`hors outil` · `contournement canal` · `rappel utilisateur` ·
`clôture prématurée` · `point d'entrée unique`

---

## Positionnement dans le Product and Service Lifecycle

### Rappel du modèle

Le Product and Service Lifecycle d'ITIL 5 comporte huit étapes : **Discover,
Design, Acquire, Build, Transition, Operate, Deliver, Support**. Il remplace la
Service Value Chain d'ITIL 4, qui en comportait six.

### Étapes mobilisées par la RFC-2026-014

| Étape | Mobilisée | Contenu dans le cas présent |
|---|---|---|
| Discover | Indirectement | Réalisée en Partie 1 : analyse des quatre dimensions et constitution du CSI Register. C'est l'amont de la RFC, pas la RFC elle-même. |
| **Design** | **Oui** | Le flux de traitement est **repensé**, pas reconfiguré : ajout d'une étape de qualification, création d'un rôle de dispatcheur, définition d'une échelle de priorité. |
| Acquire | Non | Aucune acquisition : ni licence, ni matériel, ni prestation. Le changement s'appuie sur l'outil existant. |
| **Build** | **Oui** | Paramétrage de l'outil : champ d'affectation obligatoire, alerte sur les tickets non affectés à 30 min, modèle de ticket simplifié, statut d'attente fournisseur. |
| **Transition** | **Oui** | Bascule vers le nouveau fonctionnement : pilote sur deux services, communication aux utilisateurs, formation de l'équipe au rôle de dispatcheur, point de contrôle J+15. |
| Operate | En aval | Exploitation courante une fois la généralisation effectuée. Hors périmètre de la RFC. |
| Deliver | En aval | Publication mensuelle des indicateurs de SLA définis en Partie 2. |
| Support | En aval | Traitement des demandes dans le nouveau flux, y compris au moyen de l'article KB-2026-007. |

**Les trois étapes réellement mobilisées par ce changement sont donc Design,
Build et Transition.**

### Précision sur la mobilisation de Design

Une correction de service existant se limite fréquemment à Build et Transition.
Design est ici pleinement engagé, et cela mérite d'être justifié : le changement
ne remet pas un processus en conformité avec son intention initiale, il **crée
des étapes qui n'existaient pas** — qualification à l'entrée, affectation
nominative, rôle de dispatcheur. C'est une conception, pas un correctif.

### Pourquoi ce modèle n'est pas strictement linéaire

Le Product and Service Lifecycle est un modèle de représentation, non une
séquence d'exécution obligatoire. Trois mécanismes l'établissent, tous
observables sur le cas présent.

**1. Les étapes se chevauchent.**
Le paramétrage de l'outil (Build) a commencé avant que la conception du rôle de
dispatcheur (Design) ne soit finalisée : les deux éléments sont indépendants
techniquement. Attendre la clôture complète de Design pour ouvrir Build
n'apporterait aucune sécurité et allongerait le délai sans contrepartie.

**2. Le retour en arrière est prévu par construction.**
Le CAB a imposé un point de contrôle à J+15 dont l'issue peut être un retour en
**Design** — par exemple une révision des règles d'affectation si le taux de
reclassement de priorité se révèle élevé. La boucle Transition → Design est donc
inscrite dans le plan lui-même, pas subie en cas d'échec.

**3. Le service est en Operate pendant toute la durée du changement.**
Il s'agit d'un service en fonctionnement, pas d'une création. Les étapes Operate,
Deliver et Support restent actives sans interruption pendant que Design, Build et
Transition se déroulent. Les cycles coexistent au lieu de se succéder.

**Formulation synthétique.** Le modèle décrit les activités nécessaires à la
gestion d'un produit ou d'un service sur l'ensemble de son existence, et non
l'ordre dans lequel les franchir. Un changement sur un service en production
mobilise un sous-ensemble d'étapes, dans un ordre dicté par le contexte, avec des
boucles de retour. Lire les huit étapes comme un enchaînement obligatoire
reviendrait à confondre ce modèle avec un cycle en cascade, ce qu'ITIL 5 écarte
explicitement.
