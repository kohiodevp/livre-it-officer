# 04 — Construire ses preuves

**Partie IV — CONSTRUIRE ET PRÉSENTER SES PREUVES**

Cette partie fait le lien entre le socle technique, les travaux pratiques et la
matrice de preuves. Elle apprend à transformer une pratique en élément
vérifiable, **sans fabriquer de validation**.

---

## 1. Pourquoi une compétence doit pouvoir être prouvée

Un autodidacte peut avoir beaucoup pratiqué sans disposer d'une manière claire de
démontrer ce qu'il sait faire.

Il peut avoir : installé des systèmes ; configuré des services ; écrit des
scripts ; diagnostiqué des pannes ; administré un réseau ; réalisé des
sauvegardes ; documenté des procédures.

Mais une expérience difficile à vérifier reste difficile à communiquer.

Le problème n'est donc pas seulement :

> « Est-ce que je sais faire ? »

Il devient :

> **« Qu'est-ce qui permet à une autre personne de vérifier ce que je sais
> faire ? »**

La preuve professionnelle répond à cette question.

Elle transforme une pratique personnelle en élément observable, reproductible ou
vérifiable.

---

## 2. Expérience, compétence et preuve

Ces trois notions ne doivent pas être confondues.

**Expérience** — ce qui a été vécu ou pratiqué.

**Compétence** — la capacité à mobiliser des connaissances et des pratiques pour
produire un résultat pertinent.

**Preuve** — l'élément qui permet d'établir ce résultat ou cette capacité selon
un critère défini.

La chaîne pédagogique devient :

```
expérience → pratique → compétence → preuve → formulation professionnelle
```

Mais la chaîne n'est pas automatique.

Avoir manipulé Docker ne démontre pas nécessairement la maîtrise de Docker en
production.

Avoir écrit un script Bash ne démontre pas nécessairement la capacité à
administrer une automatisation fiable.

Avoir une configuration Ansible ne démontre pas nécessairement qu'une
infrastructure complète a été déployée avec succès.

---

## 3. Un artefact n'est pas automatiquement une preuve

Un fichier peut être intéressant sans être une preuve complète.

| Artefact | Ce qu'il établit |
|---|---|
| Un script | qu'un script existe |
| Un fichier Compose | qu'une configuration est déclarée |
| Un playbook | une intention d'automatisation |
| Un README | qu'une documentation existe |
| Une capture | un état à un instant donné |

Mais ces éléments ne démontrent pas nécessairement : que le système fonctionne ;
que le résultat attendu a été obtenu ; que l'auteur sait reproduire l'opération ;
que l'opération fonctionne dans les conditions décrites.

La règle fondamentale est :

> **Un artefact n'est pas automatiquement une preuve de compétence.**

Il faut toujours demander :

> « Que permet exactement d'établir cet artefact ? »

---

## 4. Les cinq statuts de preuve

Le livre utilise cinq statuts.

| Statut | Définition |
|---|---|
| **DÉMONTRÉ** | Une preuve vérifiable, issue d'une exécution constatée, établit le résultat ou la compétence dans le périmètre considéré |
| **DÉCLARÉ** | L'information est affirmée par une personne ou un document, mais la preuve opérationnelle correspondante n'est pas encore établie |
| **INTERPRÉTÉ** | L'information résulte d'une interprétation raisonnable des éléments disponibles ; elle ne doit pas être présentée comme une observation directe |
| **OBJECTIF** | La compétence ou la pratique est visée mais reste à acquérir ou à démontrer |
| **NON ÉTABLI** | Les éléments disponibles ne permettent pas de conclure |

Ces statuts doivent rester distincts.

---

## 5. Les marqueurs de travail ne sont pas des statuts de preuve

Les marqueurs de travail utilisés dans le projet sont différents : `OBS`, `DÉD`,
`N.D.`, `BLOQUÉ`, `ÉCHEC`.

Ils décrivent l'état d'un travail ou d'une observation.

Les cinq statuts précédents qualifient une affirmation de compétence ou de preuve.

Il ne faut donc pas écrire :

> « BLOQUÉ = compétence non démontrée »

sans contexte.

Un exercice peut être bloqué pour une raison extérieure tout en laissant certaines
compétences déjà démontrées ailleurs.

La séparation des deux systèmes évite de mélanger l'état du travail avec la valeur
probante du résultat.

---

## 6. Définir la preuve avant de commencer

Un bon exercice commence par une question simple :

> **Qu'est-ce qui devra être vérifié à la fin ?**

### Mauvaise définition

> Installer Docker.

### Définition vérifiable

> Déployer un service conteneurisé, vérifier son état, accéder au service et
> documenter le résultat.

La seconde formulation donne déjà les critères de preuve.

Avant la manipulation, définir : objectif ; résultat attendu ; conditions ; méthode
de vérification ; preuve à conserver ; limites acceptables.

---

## 7. Le contrat de preuve

Pour chaque exercice, établir un petit contrat.

| Rubrique | Question |
|---|---|
| **Objectif** | Que dois-je démontrer ? |
| **Périmètre** | Dans quel environnement ? |
| **Critère** | Comment saurai-je que le résultat est correct ? |
| **Vérification** | Quelle observation permettra de le confirmer ? |
| **Preuve** | Quel artefact ou résultat sera conservé ? |
| **Limite** | Qu'est-ce qui ne sera pas démontré par cet exercice ? |

Ce contrat empêche de déplacer les critères après l'exécution.

---

## 8. Les différents types de preuves

### 8.1 Preuve d'exécution

Elle établit qu'une opération a réellement été exécutée.

Exemples : sortie de commande ; journal ; résultat de test ; historique
d'exécution.

### 8.2 Preuve de résultat

Elle établit que le résultat attendu a été obtenu.

Exemples : réponse HTTP correcte ; fichier restauré ; service accessible ; test
passant.

### 8.3 Preuve de configuration

Elle établit qu'un paramètre ou une architecture est présent.

Exemples : fichier Compose ; configuration réseau ; unité systemd ; playbook.

Cette preuve ne doit pas être confondue avec une preuve de fonctionnement.

### 8.4 Preuve de diagnostic

Elle montre la démarche suivie pour identifier un problème.

Exemples : symptôme ; hypothèses ; observations ; tests ; conclusion.

### 8.5 Preuve documentaire

Elle établit qu'une procédure ou une décision a été documentée.

La documentation reste une preuve documentaire tant que son contenu opérationnel
n'est pas vérifié.

---

## 9. La force d'une preuve dépend de la question

Il n'existe pas une preuve universelle.

| Question posée | Preuve pertinente |
|---|---|
| « Cette configuration existe-t-elle ? » | le fichier de configuration |
| « Le service fonctionne-t-il ? » | une vérification comportementale |
| « Puis-je restaurer les données ? » | une restauration réelle ou un test équivalent |
| « Puis-je reproduire cette opération ? » | une procédure et une nouvelle exécution |

Une preuve historique peut établir qu'une action a eu lieu, sans établir qu'elle
reste reproductible.

La preuve doit donc être choisie **en fonction de l'affirmation à établir**.

---

## 10. La matrice de preuve

La matrice constitue le point de liaison entre :

```
compétence → pratique → preuve → formulation
```

Pour chaque compétence, demander :

1. Quel est le périmètre ?
2. Quelle pratique correspondante ai-je réalisée ?
3. Quelle preuve existe ?
4. Quel statut est autorisé ?
5. Quelle formulation professionnelle est compatible avec ce statut ?

La matrice ne sert pas à embellir le parcours.

Elle sert à empêcher de dire davantage que ce que les preuves autorisent.

---

## 11. Partir de l'affirmation

Une méthode efficace consiste à partir de ce que l'on souhaite pouvoir dire.

> « Je sais administrer un service Linux. »

Cette phrase est trop large.

Il faut la décomposer.

Que signifie « administrer » ? Installer ; configurer ; démarrer ; arrêter ;
surveiller ; diagnostiquer ; sécuriser ; sauvegarder ; restaurer ; documenter.

Une preuve portant uniquement sur l'installation ne suffit donc pas nécessairement
à établir l'ensemble de cette compétence.

---

## 12. Réduire une compétence à un résultat observable

Une compétence devient plus facile à démontrer lorsqu'elle est formulée comme une
action observable.

### Trop large

> Je maîtrise le réseau.

### Plus précis

> Je sais diagnostiquer une absence de connectivité entre deux machines dans un
> réseau local.

### Encore plus précis

> Je peux vérifier l'interface, l'adressage, la route, le port et le service afin
> de localiser l'étape où la communication échoue.

La seconde formulation permet de construire un exercice.

La troisième permet de construire une preuve.

---

## 13. La preuve minimale utile

Une bonne preuve n'est pas nécessairement volumineuse.

Elle doit être : pertinente ; lisible ; vérifiable ; contextualisée ; suffisamment
précise.

Une capture d'écran isolée peut être insuffisante.

Un journal de 5 000 lignes peut être inutilement lourd.

Une preuve efficace contient généralement :

1. contexte ;
2. action ;
3. observation ;
4. résultat ;
5. date ou version lorsque nécessaire ;
6. limite éventuelle.

---

## 14. Le contexte est une partie de la preuve

Une sortie de commande sans contexte peut être difficile à interpréter.

```text
status: active
```

ne permet pas nécessairement de savoir : quel service ; sur quelle machine ; à
quel moment ; dans quelle configuration ; avec quel résultat fonctionnel.

La preuve doit permettre de répondre à :

> **Qu'est-ce qui a été observé, où, quand et dans quelles conditions ?**

---

## 15. Avant, pendant, après

### Avant

Documenter : environnement ; versions pertinentes ; état initial ; objectif ;
hypothèses.

### Pendant

Conserver : commandes utiles ; observations ; erreurs ; décisions ; changements
autorisés.

### Après

Conserver : résultat ; vérification ; limites ; preuve finale ; conclusion.

Cette structure permet aussi de reconstruire le raisonnement.

---

## 16. Une preuve doit être reproductible lorsque c'est pertinent

Une preuve historique peut établir qu'une action a été réalisée.

Elle ne garantit pas automatiquement qu'elle peut être reproduite.

La reproductibilité demande notamment : environnement connu ; dépendances
identifiées ; procédure disponible ; configuration maîtrisée ; résultat vérifiable.

La différence est importante :

> **« Je l'ai fait une fois »**

n'est pas toujours équivalent à :

> **« Je sais le refaire dans les mêmes conditions. »**

---

## 17. Produire une preuve sans dégrader l'environnement

La production de preuve doit respecter le périmètre de travail.

Un audit en lecture seule ne doit pas devenir une modification simplement parce
qu'une preuve manque.

Si une commande crée des fichiers temporaires, il faut choisir une méthode qui
respecte le périmètre autorisé.

Si un outil d'audit ne fonctionne pas, il faut chercher une méthode d'observation
alternative.

Il ne faut pas : créer arbitrairement un fichier dans le dépôt audité ; supprimer
un artefact préexistant pour nettoyer le résultat ; modifier la configuration
uniquement pour obtenir une preuve ; lancer un déploiement non autorisé.

La qualité de la preuve dépend aussi de l'intégrité de la méthode utilisée pour la
produire.

---

## 18. Les erreurs deviennent des preuves lorsqu'elles sont documentées

Une erreur n'est pas automatiquement un échec pédagogique.

Elle peut devenir une preuve de compétence si l'apprenant sait : reproduire le
problème ; décrire le symptôme ; formuler des hypothèses ; tester ; identifier la
cause lorsque cela est possible ; appliquer une correction autorisée ; vérifier le
résultat ; documenter la limite.

Un échec correctement documenté peut donc produire une expérience professionnelle
utile.

Mais il ne doit pas être transformé artificiellement en succès.

---

## 19. Exemple — Docker

### Affirmation

> « Je sais utiliser Docker Compose. »

### Preuve insuffisante

Un fichier `docker-compose.yml`.

### Preuve plus complète

configuration ; validation syntaxique ; démarrage ; état des conteneurs ; accès au
service ; vérification du comportement ; arrêt ou récupération ; documentation.

La configuration établit la présence d'une définition.

L'exécution et la vérification établissent davantage.

---

## 20. Exemple — Ansible

### Affirmation

> « Je sais déployer avec Ansible. »

### Preuve insuffisante

Un playbook présent dans un dépôt.

### Preuve plus complète

inventaire ; variables nécessaires ; playbook ; environnement cible ; exécution ;
résultat ; idempotence lorsque pertinente ; vérification du système cible ;
procédure de reproduction.

Si l'inventaire nécessaire n'existe pas ou si l'exécution n'a jamais été réalisée,
il faut conserver cette limite.

---

## 21. Exemple — scripts d'administration

La présence de plusieurs scripts Bash constitue un élément intéressant.

Elle peut établir : l'existence du code ; sa structure ; certaines conventions ;
certaines dépendances déclarées ou observables.

Elle ne démontre pas automatiquement : leur fonctionnement dans l'environnement
cible ; leur robustesse ; leur résultat ; leur reproductibilité ; la capacité de
l'auteur à les maintenir en production.

Pour construire une preuve plus forte :

1. sélectionner un script ;
2. définir un environnement de test ;
3. définir un résultat attendu ;
4. exécuter ;
5. vérifier ;
6. documenter ;
7. conserver la sortie.

---

## 22. Exemple — projet Android hors ligne

Un projet peut déclarer une architecture Android avec Python et Chaquopy.

La présence de fichiers de configuration et de modules Python établit certains
éléments de structure.

Elle ne démontre pas nécessairement : la construction de l'APK ; l'exécution sur
un appareil ; le fonctionnement GPS ; le fonctionnement hors ligne ; la
synchronisation ; la compatibilité de toutes les dépendances.

La preuve doit suivre la question.

Pour démontrer le fonctionnement d'une application hors ligne, une configuration
Gradle seule n'est pas suffisante.

---

## 23. Exemple — kiosque autonome

Une documentation peut décrire : Raspberry Pi ; batterie ; navigateur en mode
kiosque ; synchronisation différée ; fonctionnement local.

Cela constitue une documentation de conception.

Si les artefacts exécutables correspondants ne sont pas présents ou si aucun test
n'a été réalisé, il ne faut pas transformer cette documentation en preuve
d'exploitation.

La bonne formulation est alors limitée à ce qui est établi.

---

## 24. Démontré, déclaré, objectif : exemples de formulation

### DÉMONTRÉ

> « J'ai déployé le service dans l'environnement de test, vérifié son état et
> effectué une requête fonctionnelle. »

### DÉCLARÉ

> « Le projet documente une architecture de déploiement avec ce service. »

### INTERPRÉTÉ

> « Les artefacts disponibles suggèrent que cette architecture devait fonctionner
> de cette manière. »

### OBJECTIF

> « Je dois encore produire une preuve d'exécution de cette architecture. »

### NON ÉTABLI

> « Je ne dispose pas actuellement d'élément permettant d'établir que ce composant
> a fonctionné dans les conditions décrites. »

Ces formulations protègent la crédibilité professionnelle.

---

## 25. Transformer une pratique en fiche de preuve

### Identification

```
compétence   : ______________________
exercice     : ______________________
date         : ______________________
environnement: ______________________
```

### Objectif

```
résultat attendu : ______________________
```

### Préconditions

```
matériel    : ______________________
système     : ______________________
dépendances : ______________________
configuration: _____________________
```

### Action

```
procédure          : ______________________
commandes importantes: ___________________
```

### Vérification

```
contrôle 1 : ______________________
contrôle 2 : ______________________
contrôle 3 : ______________________
```

### Résultat

```
obtenu     : ______________________
non obtenu : ______________________
```

### Preuve conservée

```
fichier : ______________________
sortie  : ______________________
journal : ______________________
capture : ______________________
test    : ______________________
```

### Limites

```
non vérifié          : ______________________
dépendance restante : ______________________
environnement particulier : _________________
```

### Statut

```
DÉMONTRÉ   : ______________________
DÉCLARÉ    : ______________________
INTERPRÉTÉ : ______________________
OBJECTIF   : ______________________
NON ÉTABLI : ______________________
```

---

## 26. Construire une démonstration reproductible

Une démonstration professionnelle doit pouvoir être suivie par une autre personne.

### 1. Contexte

Décrire l'environnement.

### 2. Objectif

Décrire le résultat attendu.

### 3. Préparation

Présenter les prérequis.

### 4. Exécution

Réaliser les actions nécessaires.

### 5. Vérification

Démontrer le résultat.

### 6. Diagnostic

Expliquer les éventuelles anomalies.

### 7. Conclusion

Dire précisément ce qui est établi.

### 8. Limites

Dire ce qui n'a pas été démontré.

---

## 27. La démonstration courte

Pour un entretien ou une présentation, la preuve doit pouvoir être résumée.

```
Contexte → problème ou objectif → action → vérification → résultat → limite
```

### Canevas

> « Dans [contexte], mon objectif était de [objectif]. J'ai [action]. J'ai vérifié
> [critère]. Le résultat observé était [résultat]. La limite de cette démonstration
> est [limite]. »

Ce canevas ne doit être rempli qu'avec des faits réellement établis.

---

## 28. Préparer une preuve pour un entretien

L'entretien ne doit pas conduire à exagérer une compétence.

Une réponse solide peut distinguer : ce qui a été réalisé ; ce qui a été observé ;
ce qui a été appris ; ce qui reste à approfondir.

Par exemple :

> « J'ai réalisé cet exercice dans un environnement de laboratoire. J'ai vérifié le
> fonctionnement du service et documenté la procédure. Je n'ai pas encore validé ce
> même scénario en production. »

Cette formulation est plus crédible qu'une affirmation plus large que la preuve
disponible.

---

## 29. Le modèle STAR+ comme outil de présentation

Les ressources de préparation à l'entretien proposent une logique de récit
structurée.

Elle peut être adaptée aux preuves techniques :

| Temps | Contenu |
|---|---|
| **Situation** | contexte |
| **Tâche** | objectif |
| **Action** | travail réalisé |
| **Résultat** | résultat vérifié |
| **Preuve** | élément conservé |
| **Limite** | ce qui reste non établi |
| **Apprentissage** | ce qui a été acquis ou doit être approfondi |

Le « + » est important.

Il empêche le récit de s'arrêter au résultat déclaré.

Une expérience professionnelle devient plus exploitable lorsque l'apprenant peut
montrer :

> **ce qu'il a fait + comment il l'a vérifié + ce qu'il a appris + ce qu'il ne
> prétend pas encore maîtriser.**

---

## 30. Construire une preuve à partir des projets existants

Les quatre projets du laboratoire fournissent des situations différentes.

### `pi-kiosk-offline`

Les audits établissent surtout une documentation de conception dans le dépôt
considéré.

La preuve opérationnelle du kiosque n'est pas établie par cet audit.

Le travail pédagogique consiste donc à distinguer : architecture décrite ;
composants attendus ; composants réellement présents ; fonctionnement vérifié.

### `infra-as-code`

La présence de Compose, d'Ansible et de rôles fournit des artefacts techniques.

Mais l'inventaire de production est insuffisant pour établir une exécution
complète et reproductible de l'infrastructure.

La preuve doit donc porter sur une exécution réellement réalisable et vérifiée.

### `scripts-admin`

Les scripts constituent un ensemble de code réel et structuré.

L'audit a cependant distingué la présence des scripts de leur exécution et de leur
validation opérationnelle.

Une démonstration ciblée peut donc produire une preuve plus forte.

### `geo-android-offline`

Le projet contient une structure Gradle/Chaquopy et plusieurs modules Python.

L'audit n'a pas établi la construction d'un APK ni le fonctionnement complet de
l'application.

Une preuve future doit donc vérifier séparément les étapes de construction,
d'exécution et de comportement hors ligne.

---

## 31. Le cas des lacunes

Une lacune n'est pas un élément à cacher.

Elle peut devenir un objectif pédagogique.

> « La configuration existe mais son exécution n'a pas été vérifiée. »

Cette phrase permet de définir un exercice :

> « Exécuter la configuration dans un environnement contrôlé et produire une preuve
> du résultat. »

La lacune devient alors un **travail de professionnalisation**.

Elle ne devient pas rétroactivement une compétence démontrée.

---

## 32. Les preuves négatives

Il existe aussi des observations importantes qui montrent l'absence d'un élément.

Exemples : aucun test trouvé ; aucun APK produit ; aucun inventaire exploitable ;
aucun service correspondant observé ; aucune preuve d'exécution disponible.

Ces constats ne démontrent pas nécessairement que le système n'a jamais fonctionné.

Ils démontrent que **la preuve recherchée n'est pas disponible dans le périmètre
observé**.

Cette nuance doit être conservée.

---

## 33. Les preuves doivent être datées et contextualisées

Une preuve peut perdre sa valeur si son contexte disparaît.

Lorsque nécessaire, conserver : date ; version ; environnement ; branche ;
configuration pertinente ; résultat ; méthode de vérification.

Une ancienne preuve peut rester utile comme historique.

Elle ne doit cependant pas être présentée comme preuve de l'état actuel sans
vérification correspondante.

---

## 34. Construire un dossier de preuve

Pour chaque compétence importante, constituer un petit dossier :

```text
preuve/
├── README.md
├── contexte.md
├── procedure.md
├── verification.txt
├── resultats/
└── limites.md
```

La structure exacte peut varier.

Le principe reste :

> **un tiers doit pouvoir comprendre ce qui a été démontré sans devoir reconstruire
> toute l'histoire du projet.**

---

## 35. La preuve et la reproductibilité

Une preuve professionnelle devient particulièrement utile lorsqu'elle peut être
reproduite.

Pour chaque démonstration, demander : quelqu'un d'autre peut-il comprendre la
procédure ; les prérequis sont-ils connus ; les dépendances sont-elles identifiées ;
le résultat attendu est-il explicite ; le test est-il observable ; les limites
sont-elles documentées.

Si plusieurs réponses sont négatives, la preuve peut rester valable pour une
observation historique mais être insuffisante pour démontrer une capacité
reproductible.

---

## 36. L'exercice final — produire une preuve complète

Choisir une compétence parmi la matrice.

### Étape 1 — Formuler

> « Je veux démontrer que je sais… »

### Étape 2 — Définir

environnement ; prérequis ; résultat attendu ; critères d'acceptation.

### Étape 3 — Exécuter

Réaliser l'exercice.

### Étape 4 — Vérifier

Produire au moins deux contrôles pertinents.

### Étape 5 — Conserver

Enregistrer la preuve.

### Étape 6 — Limiter

Lister ce qui n'a pas été testé.

### Étape 7 — Qualifier

Attribuer le statut approprié.

### Étape 8 — Formuler

Écrire une phrase professionnelle compatible avec la preuve.

---

## 37. Critères de réussite

Une preuve complète doit permettre de répondre à cinq questions :

1. **Qu'est-ce qui devait être démontré ?**
2. **Dans quel environnement ?**
3. **Qu'est-ce qui a réellement été exécuté ?**
4. **Comment le résultat a-t-il été vérifié ?**
5. **Quelles sont les limites de la preuve ?**

Si une de ces réponses manque, la preuve doit être considérée comme incomplète ou
limitée selon le cas.

---

## 38. Ce qu'il ne faut jamais faire

Ne jamais : transformer un fichier en preuve d'exécution ; transformer une
documentation en preuve de fonctionnement ; transformer un objectif en
compétence ; transformer une interprétation en observation ; supprimer une lacune
pour améliorer un dossier ; présenter une expérience unique comme une maîtrise
générale ; cacher les conditions particulières d'un test ; utiliser une preuve
ancienne comme preuve actuelle sans contrôle ; attribuer à un projet une
fonctionnalité non vérifiée ; modifier un système uniquement pour fabriquer une
apparence de preuve.

La preuve doit augmenter la précision du parcours, pas son apparence.

---

## 39. La valeur professionnelle d'une preuve

Une preuve correctement construite permet plusieurs usages : apprendre ;
diagnostiquer ; documenter ; préparer un entretien ; présenter un portfolio ;
reprendre un projet plus tard ; transmettre une procédure ; identifier les lacunes
restantes.

Elle devient ainsi un actif professionnel.

Mais sa valeur dépend de sa fidélité à ce qui a réellement été réalisé.

---

## 40. Résultat attendu

À la fin de cette partie, l'apprenant doit savoir transformer une activité technique
en preuve exploitable.

Il doit être capable de passer de :

> « J'ai travaillé sur Docker. »

à une formulation plus précise :

> « J'ai réalisé [périmètre], dans [environnement], pour obtenir [résultat]. J'ai
> vérifié [critères] et conservé [preuve]. La démonstration ne couvre pas encore
> [limite]. »

La seconde formulation est plus longue, mais surtout plus vérifiable.

Elle permet à l'apprenant de défendre son expérience sans l'exagérer.

---

## Synthèse

Construire ses preuves consiste à rendre l'expérience vérifiable.

La chaîne centrale est :

```
COMPÉTENCE → OBJECTIF → PRATIQUE → VÉRIFICATION → PREUVE
           → STATUT → FORMULATION
```

Un fichier n'est pas automatiquement une preuve.

Une configuration n'est pas automatiquement un fonctionnement.

Une exécution n'est pas automatiquement une compétence reproductible.

Une déclaration n'est pas automatiquement une démonstration.

Une lacune n'est pas une honte à masquer.

Elle peut devenir un objectif de professionnalisation.

Le professionnel autodidacte doit donc apprendre à dire exactement :

> **« Voici ce que j'ai fait. Voici ce que j'ai observé. Voici comment je l'ai
> vérifié. Voici ce que cela démontre. Voici ce que cela ne démontre pas encore. »**

Cette discipline constitue le passage entre l'expérience personnelle et la
compétence professionnelle vérifiable.

---

## Ce que devient la fiche de preuve

La fiche que vous venez de remplir n'est pas un exercice à ranger. **Elle est le
support du discours professionnel que vous construirez dans la partie suivante.**

Une preuve non expliquée reste un document. Une preuve expliquée devient une
compétence mobilisable — non parce qu'elle est mieux présentée, mais parce que
quelqu'un d'autre peut juger de votre raisonnement et pas seulement de son
résultat.

### On n'invente pas une expérience pour en parler

C'est le point central de cette transition.

La partie suivante ne vous demande pas de raconter une expérience pour
rendre la matière plus vivante. Elle vous demande de **décrire celle que vous
venez d'établir** : la commande que vous avez réellement exécutée, le résultat
que vous avez réellement obtenu, la limite que vous n'avez pas franchie.

La section 4 l'énonce sans détour :

> **Un fichier n'est pas automatiquement une preuve.**

Et son corollaire s'applique aussi au discours :

> **Une preuve n'est pas automatiquement une explication.**

Savoir qu'un service répond localement et savoir expliquer *pourquoi* vous avez
conclu à cela, *ce que vous n'avez pas vérifié* et *ce qu'un tiers devrait
contrôler pour confirmer* sont deux compétences distinctes. La première est
acquise lorsque la commande renvoie ce que vous attendiez. La seconde s'acquiert
en la verbaliser jusqu'à ce qu'elle résiste aux questions.

### Ce qui change concrètement

À la fin de la Partie IV, vous avez un artefact vérifiable.

À la fin de la Partie V, vous aurez **le même artefact, mais expliqué** — et
surtout, la capacité de le réexpliquer dans un registre différent selon
l'interlocuteur : un collègue, un auditeur, un responsable, un recruteur.

C'est cette capacité, et non la possession d'un fichier, qui transforme une
preuve en compétence professionnelle.