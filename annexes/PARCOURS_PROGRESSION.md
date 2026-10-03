# PARCOURS DE PROGRESSION

> Ce fichier est un outil de pilotage méthodologique.
>
> Il ne constitue pas une preuve de compétence.
> Il ne remplace pas la production d'artefacts vérifiables,
> leur exécution, leur observation, leur contextualisation
> ni l'identification de leurs limites.
>
> Son objet est d'aider le lecteur à passer d'une intention
> à une compétence structurée, vérifiable et défendable.

---

## 1. Principe cardinal

**Progresser, ce n'est pas accumuler des intentions. C'est faire passer une compétence
d'un statut à un autre par des vérifications situées dans un périmètre défini.**

La progression ne se mesure pas au nombre de sujets étudiés, ni d'heures passées, ni
d'outils connus. Elle se mesure à un déplacement observable : une ligne qui change de
statut dans la matrice, parce qu'une vérification a été produite dans un périmètre
nommé.

C'est pourquoi ce fichier ne propose pas de niveaux, ni dscores, ni de paliers à franchir.
Le livre ne connaît que cinq états, décrits au § 2, et les passages qui les relient.

Un point de vocabulaire, avant de commencer. Dans le livre, une **compétence** est ce que
l'on sait comprendre, réaliser, raisonner ou expliquer ; une **preuve** est ce qui rend
cette compétence vérifiable. Le présent fichier porte sur le passage de l'un à l'autre.
Il ne dit rien de la valeur de la personne qui travaille.

---

## 2. Les statuts comme états de dossier

Les cinq statuts décrivent l'état d'un **dossier**, jamais celui d'un individu.

| Statut | État du dossier | Ce que cela implique |
|---|---|---|
| `OBJECTIF` | Cible d'apprentissage | Rien n'est encore produit ni vérifié |
| `DÉCLARÉ` | Affirmation documentée | L'exécution n'a pas été observée |
| `INTERPRÉTÉ` | Déduction à partir d'observations | Une partie du raisonnement reste indirecte |
| `DÉMONTRÉ` | Preuve vérifiable dans un périmètre | L'exécution a été constatée et contextualisée |
| `NON ÉTABLI` | Tentative de vérification insuffisante | Une information manque, ou n'a pas pu être obtenue |

Trois précisions qui évitent la plupart des malentendus.

**`DÉMONTRÉ` n'est jamais absolu.** Il vaut dans un périmètre technique — quel système,
quelle version, quel environnement — dans un périmètre temporel — quand, et pendant
combien de temps — et dans un périmètre organisationnel — pour qui, sous quelle
autorisation. Une preuve qui sort de l'un de ces trois périmètres redevient `DÉCLARÉ` pour
son destinataire, sans que la compétence soit en cause.

**`NON ÉTABLI` n'est pas un statut d'échec.** C'est un statut d'honnêteté. Il distingue la
compétence qui n'a pas été vérifiée de la compétence qui s'est révélée fausse. Les deux
se corrigent, mais par des chemins opposés : le premier demande une vérification, le
second demande une correction.

**`OBJECTIF` n'est pas une version dégradée de `DÉMONTRÉ`.** Un objectif bien formulé
vaut mieux qu'une démonstration sans périmètre. Il indique une direction de travail
légitime.

---

## 3. Transitions utiles

Ce paragraphe décrit des passages, pas des jugements. Aucun n'est obligatoire ; tous sont
réversibles.

### `OBJECTIF` → un exercice vérifiable

Un objectif devient travaillable lorsque cinq éléments sont nommés :

- une compétence visée, formulée comme un verbe d'action ;
- un périmètre — sur quoi, dans quel environnement ;
- un exercice, c'est-à-dire une action que l'on peut exécuter et observer ;
- un critère de réussite, énoncé avant l'exécution, pas après ;
- une preuve à conserver, identifiée à l'avance.

Sans ces cinq éléments, l'objectif reste une déclaration d'intention, quelle que soit sa
précision apparente.

### `DÉCLARÉ` → `INTERPRÉTÉ`

Une déclaration devient interprétation lorsque plusieurs observations permettent de
déduire un comportement, sans encore établir une preuve complète.

```
OBS : la commande retourne un résultat attendu
DÉD : le service semble fonctionner dans ce périmètre
N.D. : la persistance, la sécurité et la restauration n'ont pas été vérifiées
```

Le passage se joue sur la qualité du raisonnement, pas sur la quantité d'observations. Une
seule observation répétée dix fois reste une observation.

### `INTERPRÉTÉ` → `DÉMONTRÉ`

Une interprétation devient démonstration lorsqu'une preuve directe est produite dans un
périmètre explicite. Cinq conditions, toutes nécessaires :

- l'exécution a été observée ;
- la sortie ou l'artefact a été conservé ;
- le contexte a été précisé ;
- la vérification a été réalisée par une voie distincte de l'exécution ;
- la limite a été nommée.

La quatrième condition est la plus souvent oubliée. Vérifier en relisant son propre
résultat n'est pas vérifier : il faut une seconde voie — une commande de contrôle, un
un essai depuis un autre point, une mesure, une relecture par un pair.

### `DÉMONTRÉ` → (progression)

Une compétence démontrée n'arrête pas le cycle. Elle oriente la suite. Les directions
possibles sont :

- élargir le périmètre — un autre système, une autre version, une autre échelle ;
- tester un cas limite — le comportement en échec, la dégradation, l'interruption ;
- documenter la transmission — ce qui ferait qu'un tiers pourrait reprendre le travail ;
- faire relire par un pair, qui verra ce que l'auteur ne peut plus voir ;
- identifier ce qui reste non établi autour de cette compétence.

La progression est l'issue du cycle, puis le point de départ du suivant. Elle n'est pas un
temps de la boucle.

### Tout statut → `NON ÉTABLI`

Un statut peut revenir en arrière, et le retour n'est pas une faute. Il se produit quand :

- la preuve est perdue ou n'est plus reproductible ;
- le périmètre a changé — le système a été remplacé, la version a évolué ;
- la vérification est devenue impossible ;
- une dépendance externe bloque la validation, ce que le marqueur `BLOQUÉ` signale ;
- une tentative a échoué, ce que le marqueur `ÉCHEC` signale.

Un dossier qui ne peut que descendre n'est pas un dossier de progression. Il faut
prévoir la remontée : identifier ce qui a changé, reprendre la vérification, actualiser le
périmètre.

---

## 4. Seuil de passage

Avant de déplacer une ligne de la matrice, sept questions. Elles ne se répondent pas par
oui ou non : elles se répondent par une phrase.

```
Qu'ai-je réellement observé ?
Qu'est-ce que j'en déduis ?
Qu'est-ce qui manque encore ?
Dans quel périmètre cette affirmation tient-elle ?
Quelle preuve puis-je conserver ?
Puis-je l'expliquer sans ambiguïté ?
Quelle limite dois-je nommer ?
```

Une ligne qui ne permet pas de répondre par une phrase à la troisième question n'est pas
prête à monter d'un statut. Une ligne qui ne permet pas de répondre à la quatrième n'est
pas prête à atteindre `DÉMONTRÉ`.

Ce sont des questions d'autodiagnostic. Elles ne produisent aucun résultat : elles
révèlent ce qui manque pour pouvoir produire un résultat.

---

## 5. Jalons de progression

Cinq jalons servent de repères. Ce ne sont pas des niveaux, ni une échelle, ni une
certification. Ils marquent des moments où le dossier change de nature.

| Jalon | Objet | Preuve minimale attendue |
|---|---|---|
| J1 | Inventaire honnête | Liste des compétences visées, déclarées, interprétées, non établies |
| J2 | Première preuve d'exécution | Sortie, journal, script exécuté, résultat observé et conservé |
| J3 | Preuve de compréhension | Explication du mécanisme, du périmètre et de la limite |
| J4 | Preuve de transmission | Documentation, procédure reproductible, passation |
| J5 | Revue externe | Retour d'un pair, audit interne, ou action suivante datée |

Deux observations sur ces jalons.

Ils ne se franchissent pas dans l'ordre. On peut démontrer une compétence sans comprendre
le mécanisme qui la sous-tend, ou comprendre une chose sans l'avoir jamais exécutée. L'ordre
décrit une progression typique, pas une obligation.

J1 est le jalon le plus important et le plus souvent escamoté. Un inventaire honnête —
celui qui classe une compétence en `OBJECTIF` plutôt que de la laisser sans mention —
produit plus de progression réelle que dix démonstrations non classées.

---

## 6. Fiche de progression

Ce canevas est volontairement vide. Il appartient à celui qui l'utilise.

```
Compétence visée   :
Statut actuel      :
Périmètre considéré:
Exercice à réaliser:
Critère de réussite:
Marqueurs attendus :
Limite anticipée  :
Preuve existante   :
Ce qui manque      :
Prochaine revue    :
```

Une fiche par compétence. Une compétence large ne tient pas sur une fiche : c'est le
signal qu'elle doit être découpée.

Le champ `Critère de réussite` se remplit **avant** l'exercice. Rempli après, il ne sert
plus à rien : il ne fait que décrire ce qui a eu lieu.

---

## 7. Cycle de revue

Après chaque exercice :

- noter ce qui a été observé ;
- séparer ce qui est observé de ce qui est déduit ;
- signaler ce qui manque par `N.D.` ;
- identifier une limite ;
- définir la prochaine action.

À chaque ajout de preuve :

- mettre à jour la matrice ;
- vérifier le périmètre — technique, temporel, organisationnel ;
- contrôler la diffusabilité si le dossier est partagé ;
- replacer la compétence dans la boucle à six temps.

Il n'y a pas de fréquence imposée. Une revue mensuelle, une revue après chaque
compétence, ou une revue à chaque changement de poste sont trois usages également
valables. Ce qui compte est que la revue existe et qu'elle produise une action, pas
seulement une relecture.

Une revue qui ne fait bouger aucune ligne est une lecture, pas une revue.

---

## 8. Pièges à éviter

- **Confondre un artefact et une preuve.** Le fichier existe ; il ne prouve rien par sa
  seule présence.
- **Présenter `DÉCLARÉ` comme `DÉMONTRÉ`.** C'est la faute la plus coûteuse, parce
  qu'elle se découvre à l'entretien ou en mission.
- **Extrapoler à partir d'`INTERPRÉTÉ` sans le dire.** Une déduction juste dans son
  périmètre devient fausse dès qu'on l'élargit en silence.
- **Masquer une limite pour paraître plus compétent.** Une limite nommée vaut mieux
  qu'une compétence surdéclarée.
- **Transformer un `OBJECTIF` en compétence par intention.** Le passage du temps n'est
  pas un statut.
- **Publier une preuve sans vérifier la confidentialité.** Voir `ETHIQUE_SECURITE.md`.
- **Croire qu'une certification remplace la capacité à expliquer.** Une certification
  atteste d'un parcours, pas d'un raisonnement.
- **Oublier que `DÉMONTRÉ` vaut dans un périmètre donné.** Une preuve sans périmètre est
  une affirmation.
- **Compter les lignes de la matrice.** Le nombre de `DÉMONTRÉ` progresse moins vite que
  l'estime du lecteur ne le croit.

---

## 9. Articulation avec les autres annexes

| Annexe | Usage dans la progression |
|---|---|
| `MATRICE_PREUVES.md` | Tableau de bord des statuts |
| `COMMANDES.md` | Sources de vérifications techniques |
| `CHECKLISTS.md` | Contrôle de complétude |
| `OBJECTIFS_A_COMPLETER.md` | Suivi des cibles non encore démontrées |
| `ETHIQUE_SECURITE.md` | Contrôle avant partage |
| `EXEMPLES_PEDAGOGIQUES.md` | Illustration de méthode, non preuve personnelle |
| `PHRASE_MANIFESTE.md` | Cadre normatif du livre |
| `GLOSSAIRE.md` | Définitions des termes employés ici |

Les exemples de méthode restent dans `EXEMPLES_PEDAGOGIQUES.md`. Le présent fichier n'en
contient aucun, volontairement : il organise une progression, il n'en démontre aucune.

---

## 10. Limite de ce fichier

Ce fichier organise la progression.

Il ne prouve rien en lui-même.

Il ne remplace pas une exécution observée, une preuve conservée, une explication tenue,
une limite nommée ou une revue par un tiers compétent.

En l'absence de preuve vérifiable, le statut reste celui du dossier : déclaré, interprété,
objectif ou non établi. Aucune méthode d'organisation ne le change.
