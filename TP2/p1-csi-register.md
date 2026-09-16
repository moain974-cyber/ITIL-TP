# Partie 1 — Diagnostic du service helpdesk interne

## Méthode d'analyse

Le contexte fournit trois symptômes exprimés par les utilisateurs : lenteur de
traitement, tickets perdus, rappels multiples sur un même problème. Ces éléments
décrivent un ressenti, pas une cause.

L'analyse ci-dessous remonte donc de chaque symptôme vers les défaillances qui le
produisent, en répartissant ces défaillances sur les quatre dimensions du
service. Cette grille garantit que le diagnostic ne se limite pas au volet
outillage, qui est le réflexe habituel face à ce type de plainte.

### Rattachement symptômes / dimensions

| Symptôme observé | Dimensions concernées |
|---|---|
| Lenteur de traitement | Value Streams & processus, Information & technologie, Partenaires & fournisseurs |
| Tickets perdus | Organisations & personnes, Information & technologie |
| Rappels multiples sur un même problème | Value Streams & processus, Information & technologie, Organisations & personnes |

Aucun symptôme ne relève d'une dimension unique : c'est l'indice que la cause
n'est pas un défaut d'outil isolé, mais un déficit de structuration du service.

---

## Constats par dimension

### Organisations & personnes

**Constat 1 — Aucun rôle d'attribution n'est formalisé.**

Les tickets entrants ne sont rattachés à un technicien qu'au volontariat. Un
ticket que personne ne prend spontanément ne fait donc l'objet d'aucune prise en
charge, et surtout d'aucune alerte : il sort silencieusement du flux. C'est le
mécanisme direct des tickets perdus signalés par les utilisateurs.

Le problème n'est pas un manque d'implication individuelle mais une absence de
responsabilité assignée : tant que la prise en charge repose sur l'initiative, un
ticket peu attractif — sujet flou, utilisateur difficile, compétence rare — sera
systématiquement celui qui reste au fond de la file.

**Constat 2 — La charge est absorbée par les interruptions.**

Les rappels multiples ne sont pas seulement un symptôme, ils sont aussi une cause
aggravante. Chaque relance consomme du temps technicien sans faire progresser la
demande initiale. L'équipe traite donc une charge supérieure au volume réel de
demandes, ce qui alimente la lenteur constatée et entretient le cycle : plus
c'est lent, plus les utilisateurs relancent, plus c'est lent.

**Constat 3 — Aucune compétence n'est identifiée par domaine.**

Sans répartition des expertises, un ticket est traité par celui qui le prend, pas
par celui qui sait le traiter. Les demandes nécessitant une compétence spécifique
subissent donc soit un délai d'apprentissage, soit plusieurs réaffectations
successives — deux causes de lenteur invisibles dans les statistiques d'un outil
qui ne trace pas les réaffectations.

### Information & technologie

**Constat 1 — Il n'existe pas de point d'entrée unique.**

Les demandes arrivent par plusieurs canaux (outil de ticketing, téléphone,
sollicitation directe dans les couloirs). Celles formulées oralement ne sont pas
systématiquement saisies dans l'outil. Une demande non enregistrée est invisible :
elle ne peut ni être priorisée, ni être suivie, ni apparaître dans un indicateur.

Ce constat a une conséquence méthodologique importante : toute mesure du service
faite aujourd'hui porterait sur un périmètre partiel et sous-estimerait le volume
réel.

**Constat 2 — L'utilisateur n'a aucune visibilité sur l'avancement.**

En l'absence de notification automatique ou de portail de suivi, un utilisateur
qui a déposé une demande n'a aucun moyen de savoir si elle a été prise en charge,
ni quand elle le sera. Son unique levier est de rappeler. Le symptôme des rappels
multiples n'est donc pas un comportement déviant des utilisateurs : c'est la seule
action rationnelle que le service leur laisse.

**Constat 3 — Aucune base de connaissance n'est alimentée.**

Les résolutions passées ne sont pas capitalisées. Un problème déjà rencontré est
re-diagnostiqué intégralement à chaque occurrence, y compris lorsqu'il a déjà été
résolu par un collègue la semaine précédente. Cela allonge mécaniquement le délai
de traitement et rend le service dépendant de la mémoire individuelle des
techniciens présents.

### Partenaires & fournisseurs

> ⚠️ Dimension non documentée dans le contexte fourni. Constats établis par
> déduction — à confirmer ou remplacer selon les éléments donnés en cours.

**Constat 1 — Les dépendances externes ne sont pas encadrées par un engagement de
délai.**

Une partie des tickets ne peut être close sans l'intervention d'un tiers
(maintenance matérielle, éditeur applicatif, opérateur réseau). Aucun délai de
réponse n'étant contractualisé avec ces intervenants, le helpdesk subit leur
temps de traitement sans pouvoir s'engager auprès de ses propres utilisateurs.

**Constat 2 — L'attente fournisseur n'est pas matérialisée dans l'outil.**

Faute de statut dédié, un ticket bloqué chez un prestataire reste affiché comme un
ticket ouvert ordinaire. Deux effets se combinent : l'utilisateur constate une
absence de progression et relance, alors qu'aucune action n'est possible côté
interne ; et les indicateurs de délai imputent au helpdesk un temps d'attente dont
il n'est pas responsable.

### Value Streams & processus

**Constat 1 — Le flux ne comporte pas d'étape de qualification à l'entrée.**

Aucune priorité n'est attribuée à la création du ticket. Les demandes sont donc
traitées dans leur ordre d'arrivée, indépendamment de leur urgence réelle. Une
demande bloquante pour un service entier attend derrière une demande de confort
déposée plus tôt. C'est la cause principale de la lenteur perçue : le délai moyen
peut être correct alors que les demandes critiques, elles, sont traitées trop
tard.

**Constat 2 — Le flux ne comporte pas d'étape de clôture validée.**

Un ticket est fermé sur la seule appréciation du technicien, sans confirmation de
l'utilisateur. Une résolution partielle ou inadaptée est donc comptabilisée comme
un succès. Le problème réapparaît ensuite sous la forme d'une demande nouvelle,
sans lien avec la précédente : c'est le mécanisme des rappels sur un même sujet,
et il fausse simultanément les statistiques de résolution.

**Constat 3 — Aucune boucle de retour n'alimente l'amélioration.**

Les tickets récurrents ne déclenchent aucune analyse. Le service traite donc
indéfiniment les mêmes causes au lieu de les éliminer, ce qui maintient un volume
de demandes structurellement élevé et entretient les trois symptômes.

---

## CSI Register

| # | Amélioration | Effort | Impact | Priorité |
|---|---|---|---|---|
| 1 | Instaurer un point d'entrée unique avec attribution obligatoire dès la création du ticket (rôle de dispatcheur tournant) | Moyen | Fort | 1 |
| 2 | Ajouter une étape de clôture conditionnée à la confirmation de l'utilisateur | Faible | Moyen | 2 |
| 3 | Constituer une base de connaissance alimentée à partir des tickets récurrents | Moyen | Fort | 3 |

### Justification des évaluations

**Amélioration 1 — Effort moyen, impact fort.**
L'effort est moyen et non faible : la mesure est peu coûteuse techniquement
(paramétrage et règle d'affectation) mais suppose un changement d'habitude
collectif, à savoir refuser de traiter une demande hors outil. C'est la conduite
du changement qui pèse, pas la mise en œuvre. L'impact est fort car la mesure agit
sur deux symptômes sur trois : elle supprime la cause des tickets perdus et rend
le volume réel mesurable.

**Amélioration 2 — Effort faible, impact moyen.**
L'effort est faible : il s'agit d'ajouter un statut intermédiaire et une
notification dans un flux existant, sans réorganisation. L'impact est qualifié de
moyen et non de fort car la mesure traite une cause de rappel — la clôture
prématurée — mais pas les autres : un utilisateur sans visibilité sur l'avancement
continuera de relancer avant même la clôture.

**Amélioration 3 — Effort moyen, impact fort.**
L'effort est moyen car la difficulté n'est pas de créer la base mais de la
maintenir : la rédaction d'articles doit devenir une étape du traitement, sinon la
base se périme en quelques mois. L'impact est fort car la mesure réduit le temps
de diagnostic sur tous les sujets récurrents et rend le service moins dépendant
des personnes présentes.

### Justification de la priorisation

La priorisation ne découle pas mécaniquement du rapport effort/impact. Les
améliorations 1 et 3 présentent le même couple (moyen / fort), et c'est une
contrainte de séquence qui les départage.

**L'amélioration 1 est un prérequis aux deux autres.** Tant que des demandes
circulent hors de l'outil, aucune donnée fiable n'existe sur le service : ni les
délais réels, ni le volume réel, ni l'identification des problèmes véritablement
récurrents. Construire une base de connaissance sur un historique incomplet
reviendrait à documenter les sujets les plus tracés plutôt que les plus fréquents.

**L'amélioration 2 passe en second malgré un impact moindre** car son effort est
faible et son effet immédiat. Elle ne nécessite ni donnée préalable ni
réorganisation, et coupe une source de rappels dès sa mise en place. La reporter
n'apporterait aucun bénéfice.

**L'amélioration 3 est placée en troisième position** non par manque d'intérêt
mais parce que son bénéfice est différé : elle suppose un historique de tickets
exploitable, donc la mise en œuvre effective de l'amélioration 1 et un délai
d'accumulation de données.

---

## Principe directeur mobilisé

### Principe retenu : « Collaborer et promouvoir la visibilité »

Les trois symptômes du contexte sont, ramenés à leur mécanisme, trois défauts de
visibilité :

- un ticket non attribué n'est visible de personne dans l'équipe, donc il se
  perd ;
- l'utilisateur ne voit pas l'avancement de sa demande, donc il rappelle ;
- le technicien ne voit pas les résolutions passées, donc il reprend le diagnostic
  depuis le début et le traitement s'allonge.

Ce constat a directement structuré la priorisation. Les trois améliorations ont
été ordonnées selon la portée de la visibilité qu'elles créent : d'abord au sein
de l'équipe (attribution tracée), puis vers l'utilisateur (clôture confirmée),
puis vers les traitements futurs (base de connaissance).

Un point mérite d'être souligné : aucune des trois améliorations retenues n'ajoute
de capacité technique nouvelle au service. Toutes se contentent de rendre
observable ce qui se déroulait déjà à l'aveugle. C'est la marque de ce principe
directeur — le dysfonctionnement analysé ne relevait pas d'un manque de moyens,
mais d'un manque de transparence du flux.

### Principe écarté : « Optimiser et automatiser »

Ce principe aurait conduit à chercher d'emblée une solution d'outillage —
affectation automatique, réponses pré-rédigées, tri algorithmique des demandes. Il
a été écarté parce qu'il est prématuré : ITIL recommande de ne pas automatiser un
processus qui n'est pas d'abord défini et maîtrisé. Automatiser l'affectation de
tickets dans un service où une partie des demandes n'est même pas enregistrée
reviendrait à optimiser un flux partiel, et à figer le contournement existant
plutôt qu'à le corriger.
