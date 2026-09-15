# Partie 2 — Pilotage du service (Service Level Management + Event Management)

## Préambule — Échelle de priorité retenue

Les SLA demandés devant être déclinés par niveau de priorité, l'échelle utilisée
est définie au préalable. La priorité est calculée en croisant l'**impact**
(nombre d'utilisateurs concernés) et l'**urgence** (caractère bloquant pour
l'activité).

| Niveau | Libellé | Critère de déclenchement | Exemple |
|---|---|---|---|
| **P1** | Critique | Service indisponible pour plusieurs utilisateurs, ou activité métier totalement bloquée | Portail de tickets injoignable, serveur de fichiers hors service |
| **P2** | Majeur | Fonctionnalité dégradée ou utilisateur unique bloqué, contournement possible | Poste ne démarre plus, imprimante de service en panne |
| **P3** | Normal | Demande sans blocage de l'activité | Demande d'accès applicatif, installation de logiciel |

Cette échelle répond directement au constat de la Partie 1 : l'absence d'étape de
qualification à l'entrée du flux. Sans priorité attribuée, aucun SLA différencié
n'est mesurable, puisque toutes les demandes sont traitées dans leur ordre
d'arrivée.

---

## SLA 1 — Délai de première réponse

**Définition.** Durée écoulée entre l'enregistrement du ticket et le premier
retour qualifié au demandeur : accusé de prise en charge nominatif, indiquant le
technicien affecté et le délai de résolution estimé.

Un accusé de réception automatique généré par l'outil n'est **pas** considéré
comme une première réponse : il n'engage personne et ne réduit pas le besoin de
relance de l'utilisateur.

| Priorité | Engagement de délai | SLO associé |
|---|---|---|
| P1 | 30 minutes | 95 % des tickets P1 reçoivent une première réponse en moins de 30 min sur un mois glissant |
| P2 | 2 heures ouvrées | 90 % des tickets P2 reçoivent une première réponse en moins de 2 h ouvrées |
| P3 | 1 jour ouvré | 90 % des tickets P3 reçoivent une première réponse en moins de 1 jour ouvré |

**Justification du choix de cet indicateur.** Ce SLA a été retenu en premier
parce qu'il traite la cause du symptôme le plus coûteux identifié en Partie 1 :
les rappels multiples. Un utilisateur relance quand il ne sait pas où en est sa
demande. Garantir un retour nominatif rapide supprime le motif de la relance,
même lorsque la résolution elle-même prend du temps.

---

## SLA 2 — Délai de résolution

**Définition.** Durée écoulée entre l'enregistrement du ticket et la restauration
du service pour le demandeur, confirmée par ce dernier.

La clôture n'est prononcée qu'après confirmation de l'utilisateur, conformément
à l'amélioration n° 2 du CSI Register. Une résolution non confirmée sous 3 jours
ouvrés est clôturée automatiquement, avec mention explicite dans le ticket.

| Priorité | Engagement de délai | SLO associé |
|---|---|---|
| P1 | 4 heures | 90 % des tickets P1 résolus en moins de 4 h sur un mois glissant |
| P2 | 1 jour ouvré | 90 % des tickets P2 résolus en moins de 1 jour ouvré |
| P3 | 5 jours ouvrés | 85 % des tickets P3 résolus en moins de 5 jours ouvrés |

**Justification des taux retenus.** Les SLO ne sont volontairement pas fixés à
100 %. Un engagement à 100 % est intenable dès qu'un aléa survient (absence,
pic de charge, dépendance externe) et conduit mécaniquement à une dégradation de
la relation de service : soit l'engagement est tenu au détriment de la qualité de
résolution, soit il est affiché comme non tenu en permanence et perd toute valeur
de pilotage.

Le taux décroît avec la priorité (95 % → 90 % → 85 %) parce que la tolérance au
dépassement croît à mesure que l'impact décroît.

---

## Conditions d'application communes aux deux SLA

Ces conditions sont indispensables pour que les engagements soient mesurables et
opposables.

### Plage de service

Les délais exprimés en heures ouvrées courent du lundi au vendredi, de 8 h à
18 h, hors jours fériés. Un ticket P2 déposé à 17 h 30 a donc pour échéance de
première réponse 9 h 30 le lendemain ouvré.

Les délais des tickets P1 courent en heures calendaires sur la plage de service
uniquement : aucune astreinte n'est couverte par le présent accord.

### Exclusions du décompte

Le chronomètre est suspendu dans deux cas :

- **Attente demandeur** : information complémentaire sollicitée auprès de
  l'utilisateur et non fournie.
- **Attente fournisseur** : ticket en dépendance d'un intervenant externe.

Cette seconde exclusion répond directement au constat établi en Partie 1 sur la
dimension *Partenaires & fournisseurs*. Sans elle, le helpdesk se verrait imputer
un délai sur lequel il n'a aucun levier, ce qui rendrait le SLA injuste et donc
inexploitable comme outil de pilotage.

L'exclusion n'est recevable que si le statut correspondant est renseigné dans
l'outil. Un ticket bloqué chez un prestataire mais laissé en statut « en cours »
reste décompté.

### Méthode de mesure

Les indicateurs sont calculés automatiquement depuis l'outil de ticketing, sur un
mois glissant, et publiés mensuellement.

Un point de vigilance méthodologique doit être signalé : ces mesures ne portent
que sur les demandes enregistrées. Tant que l'amélioration n° 1 du CSI Register
(point d'entrée unique) n'est pas déployée, les demandes formulées par téléphone
ou de vive voix échappent au décompte. **Les SLA ne sont donc réellement
opposables qu'une fois ce prérequis mis en œuvre** — ce qui confirme a posteriori
la priorisation retenue en Partie 1.

---

## Classification des événements (pratique Event Management)

### Critère de discrimination appliqué

Le tri entre les trois catégories repose sur un critère unique et constant :
**l'existence d'un impact avéré sur le service rendu à l'utilisateur, au moment
où l'événement est journalisé.**

| Catégorie | Critère | Conséquence |
|---|---|---|
| **Informational** | Événement conforme au fonctionnement nominal | Journalisation seule, aucune action |
| **Warning** | Seuil approché ou franchi, service encore rendu | Action préventive planifiée |
| **Exception** | Service dégradé ou interrompu, maintenant | Action immédiate, ouverture d'un Incident |

La distinction Warning / Exception ne dépend donc **ni de la gravité potentielle**,
ni de la nature technique de l'événement, mais du fait que l'utilisateur subit ou
non une dégradation à l'instant du log.

### Tableau de classification

| # | Log | Classification | Justification | Action déclenchée |
|---|---|---|---|---|
| 1 | `AUTH user=jdupont action=login status=success host=WKS-042` | **Informational** | Authentification réussie sur un poste identifié. Aucun écart au fonctionnement nominal. | Aucune. Conservation à des fins de traçabilité. |
| 2 | `DISK host=SRV-FILE01 usage=82% threshold=80%` | **Warning** | Le seuil de 80 % est franchi, mais le serveur reste opérationnel : aucun utilisateur n'est affecté à cet instant. | Planifier une purge des données obsolètes et une analyse de la croissance d'occupation sous 5 jours ouvrés. Placer une alerte à 90 % qui, elle, déclenchera une Exception. |
| 3 | `SVC name=helpdesk-portal status=unreachable duration=00:04:12` | **Exception** | Le portail est injoignable depuis plus de 4 minutes. Impact direct et avéré : aucun utilisateur ne peut déposer de demande pendant l'indisponibilité. | Ouverture immédiate d'un Incident en priorité **P1**. Vérification du service applicatif et du serveur hôte. Communication aux utilisateurs. |
| 4 | `BACKUP job=nightly-backup host=SRV-DB01 status=completed size=45GB` | **Informational** | Sauvegarde planifiée terminée avec succès, volume cohérent. Fonctionnement nominal. | Aucune. Le volume est à conserver comme référence : un futur écart significatif constituerait, lui, un Warning. |
| 5 | `NET link=switch-3F-port12 status=down flapping=true count=6/10min` | **Exception** | Voir analyse détaillée ci-dessous. | Ouverture d'un Incident en priorité **P2**. Désactivation administrative du port pour stabiliser le lien, puis diagnostic physique. |

### Analyse détaillée du log n° 5

Ce log est le seul dont la classification ne se lit pas directement, et il mérite
d'être argumenté.

**L'hypothèse Warning est défendable.** Un port réseau n'est pas un service : son
instabilité pourrait être lue comme un signal précurseur d'une panne matérielle à
venir, appelant une action préventive avant que l'utilisateur ne soit affecté.

**Elle est néanmoins écartée, pour trois raisons.**

1. **L'impact est déjà réalisé.** Le champ `status=down` décrit un état constaté,
   pas un seuil approché. À chaque cycle de bascule, la connectivité de
   l'équipement raccordé est effectivement interrompue.

2. **La répétition établit le caractère avéré.** Six occurrences en dix minutes
   éliminent l'hypothèse de l'incident isolé et caractérisent une instabilité
   installée. Un `status=down` unique et non répété relèverait effectivement du
   Warning.

3. **Le mode de défaillance est plus pénalisant qu'une panne franche.** Un lien
   qui bascule alternativement ne déclenche pas les mécanismes de bascule
   automatique et ne produit pas de plainte claire : l'utilisateur subit des
   coupures intermittentes qu'il attribue généralement à son poste. Cette
   ambiguïté génère précisément le type de demandes mal qualifiées et
   re-déposées plusieurs fois qui figure parmi les symptômes de la Partie 1.

**Justification de la priorité P2 et non P1.** Un seul port est concerné, donc un
périmètre d'utilisateurs restreint, et un contournement immédiat existe (report
sur un autre port du commutateur). Le critère P1 — plusieurs utilisateurs
bloqués sans contournement — n'est pas rempli.

### Remarque sur l'articulation avec les autres pratiques

Deux des cinq événements déclenchent l'ouverture d'un Incident. Cela illustre la
frontière entre les pratiques : **Event Management détecte et qualifie**,
**Incident Management traite**. Un événement classé Exception ne constitue pas un
incident en lui-même ; il en déclenche l'ouverture.

Par ailleurs, si le log n° 5 se reproduisait sur d'autres ports du même
commutateur, le traitement relèverait de **Problem Management** : la répétition
sur plusieurs occurrences suggère une cause commune, qu'un traitement en
incidents successifs ne permettrait pas d'éliminer.
