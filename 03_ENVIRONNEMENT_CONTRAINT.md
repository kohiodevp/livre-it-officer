# 03 — Environnement contraint

**Partie III — OPÉRER DANS UN ENVIRONNEMENT CONTRAINT**

Cette partie apprend à travailler sous contrainte réelle — ressources limitées,
réseau intermittent, absence d'Internet, disponibilité à préserver. Les lacunes
des sources restent des **lacunes** : elles ne deviennent pas des compétences
acquises par la seule lecture.

---

## 1. Pourquoi apprendre sous contrainte

Un professionnel de l'informatique ne travaille pas toujours dans un
environnement idéal.

Le matériel peut être limité.
Le réseau peut être intermittent.
L'accès à Internet peut être absent.
Les ressources CPU, mémoire ou stockage peuvent être réduites.
Un service peut devoir fonctionner avec peu de dépendances.
Une intervention peut devoir être réalisée sans interrompre inutilement ce qui
fonctionne déjà.

Ces situations ne constituent pas seulement des difficultés techniques.

Elles obligent à raisonner.

Un environnement contraint apprend à répondre à des questions fondamentales :

- De quelles ressources est-ce que je dispose réellement ?
- De quoi mon système dépend-il ?
- Que puis-je faire sans réseau ?
- Que puis-je vérifier localement ?
- Que puis-je restaurer si une dépendance disparaît ?
- Quelle information dois-je documenter avant d'agir ?
- Quelle modification est réellement nécessaire ?
- Comment prouver que mon système fonctionne ?

L'objectif n'est donc pas d'apprendre à « bricoler ».

L'objectif est d'apprendre à **adapter une pratique professionnelle à des
contraintes réelles sans perdre la maîtrise du système**.

---

## 2. La contrainte comme méthode d'apprentissage

Une contrainte transforme une tâche ordinaire en problème à résoudre.

> « Installer un service Web »

est une tâche technique.

Mais :

> « Faire fonctionner un service Web sur une machine disposant de peu de
> ressources, avec une connectivité limitée, puis vérifier son fonctionnement sans
> dépendre d'un service externe »

est un exercice de raisonnement.

La seconde situation oblige à distinguer :

1. le besoin ;
2. les ressources disponibles ;
3. les dépendances ;
4. l'installation ;
5. la configuration ;
6. le démarrage ;
7. le fonctionnement réel ;
8. la vérification ;
9. la récupération ;
10. la documentation.

Cette séquence est transférable à de nombreux domaines de l'informatique.

---

## 3. Les quatre contraintes principales

Pour apprendre à travailler sous contrainte, on peut commencer par quatre familles.

### 3.1 Contrainte matérielle

La machine possède une quantité limitée de : CPU, mémoire, stockage, énergie,
interfaces réseau, périphériques.

La première compétence consiste à **mesurer avant de conclure**.

Questions de travail :

- Combien de processeurs sont disponibles ?
- Quelle quantité de mémoire est disponible ?
- Quelle quantité de stockage reste disponible ?
- Quels périphériques sont détectés ?
- Quels processus consomment les ressources ?
- Quelles ressources sont réellement nécessaires au service ?

Une machine lente n'est pas automatiquement une machine insuffisante.

Il faut d'abord établir où se situe la contrainte.

### 3.2 Contrainte réseau

Un système peut fonctionner avec : un réseau local ; une connexion intermittente ;
une connexion limitée ; aucun accès Internet ; plusieurs segments réseau ; un
accès indirect à certains services.

Il faut donc distinguer :

```
fonctionnement local  ≠  dépendance externe
```

Un service qui fonctionne uniquement lorsque plusieurs services Internet sont
disponibles n'est pas équivalent à un service réellement autonome.

Questions de travail :

- Le service écoute-t-il localement ?
- Quelle adresse utilise-t-il ?
- Quel port utilise-t-il ?
- A-t-il besoin du DNS ?
- A-t-il besoin d'Internet ?
- Peut-il fonctionner sur un réseau isolé ?
- Quelles dépendances disparaissent lorsque la connexion est interrompue ?

---

## 4. Travailler hors ligne

Le hors-ligne est une contrainte particulièrement formatrice.

Il oblige à connaître les dépendances du système au lieu de supposer que toute
ressource sera toujours disponible.

Un environnement hors ligne peut nécessiter : des paquets déjà disponibles ; des
fichiers de configuration locaux ; une documentation locale ; des données
stockées localement ; des outils de diagnostic présents sur la machine ; des
sauvegardes accessibles sans Internet.

Mais « hors ligne » ne signifie pas nécessairement « sans réseau ».

Un système peut fonctionner sur un réseau local tout en étant totalement isolé
d'Internet.

Cette distinction est importante.

### Exercice de raisonnement

Pour un service donné, établir deux colonnes :

| Dépendance | Nécessaire hors ligne ? |
|---|---|
| Système d'exploitation | À vérifier |
| DNS externe | À vérifier |
| Internet | À vérifier |
| Base de données locale | À vérifier |
| Fichiers de configuration | À vérifier |
| Documentation locale | À vérifier |
| Service distant | À vérifier |

Le tableau ne doit pas être rempli par intuition.

Chaque réponse doit être vérifiée par observation, documentation technique ou
expérimentation contrôlée.

---

## 5. Réduire les dépendances

La contrainte pousse naturellement vers la sobriété.

Une solution peut fonctionner avec dix composants alors qu'une autre n'en
nécessite que trois.

Le nombre de composants n'est toutefois pas, à lui seul, un critère de qualité.

La bonne question est :

> **Chaque dépendance est-elle nécessaire, comprise et maîtrisée ?**

Pour chaque composant, rechercher : sa fonction ; son fournisseur ; son
emplacement ; son état ; ses dépendances ; son mode de démarrage ; son mode de
diagnostic ; son mode de récupération.

Une dépendance inconnue constitue un risque de diagnostic.

Une dépendance non documentée constitue un risque de maintenance.

Une dépendance non vérifiée ne doit pas être présentée comme maîtrisée.

---

## 6. Observer avant d'agir

Sous contrainte, une modification inutile peut coûter davantage qu'en
environnement confortable.

La méthode de base reste donc :

```
observer → qualifier → décider → agir → vérifier → documenter
```

### Avant toute intervention, établir au minimum

**État initial** : système ; ressources ; réseau ; services ; processus ; stockage ;
journaux pertinents ; configuration utile.

**Objectif** — formuler précisément ce qui doit changer.

> « Le service HTTP doit être accessible depuis la machine locale sur le port
> attendu. »

Cette formulation est préférable à :

> « Il faut réparer le serveur. »

Le premier énoncé est vérifiable.

Le second ne définit pas encore le problème.

---

## 7. Démarrer n'est pas fonctionner

Un processus peut être lancé sans fournir le service attendu.

La vérification doit donc porter sur plusieurs niveaux :

1. le processus existe ;
2. le service est actif ;
3. le port attendu écoute ;
4. la requête attendue fonctionne ;
5. la réponse obtenue est correcte ;
6. les journaux ne signalent pas une erreur bloquante.

La chaîne devient :

```
processus → service → port → protocole → réponse → résultat attendu
```

Cette méthode évite de considérer un simple état `active` comme une preuve
complète.

---

## 8. Diagnostiquer avec peu d'outils

Un environnement contraint peut ne pas disposer de tous les outils habituels.

Il faut alors connaître les outils fondamentaux du système.

Pour Linux, le travail peut notamment s'appuyer sur : navigation dans le système
de fichiers ; permissions ; processus ; services ; sockets ; interfaces réseau ;
routes ; résolution DNS ; journaux ; espace disque ; mémoire ; charge système.

L'objectif pédagogique n'est pas de mémoriser une liste de commandes.

Il est de savoir **quelle observation permet de répondre à quelle question**.

> « Le service ne répond pas. »

Cette phrase ouvre plusieurs hypothèses : processus absent ; service arrêté ;
mauvais port ; mauvaise adresse ; pare-feu ; erreur applicative ; dépendance
indisponible ; ressource insuffisante.

Une bonne démarche ne choisit pas immédiatement une hypothèse.

Elle cherche l'observation qui permet de les distinguer.

---

## 9. La contrainte mémoire

La mémoire disponible influence directement les choix techniques.

Lorsqu'une application consomme trop de mémoire, plusieurs comportements
peuvent apparaître : ralentissement ; utilisation accrue du swap ; arrêt d'un
processus ; impossibilité de lancer un composant supplémentaire ; dégradation
progressive du service.

Il faut éviter une conclusion du type :

> « La machine manque de mémoire. »

tant que la mesure ne l'établit pas.

La démarche correcte est :

1. mesurer la mémoire disponible ;
2. identifier les consommateurs ;
3. observer l'évolution dans le temps ;
4. rechercher les journaux ou événements pertinents ;
5. déterminer si la mémoire constitue réellement la contrainte ;
6. seulement ensuite choisir une action.

---

## 10. La contrainte stockage

Le stockage doit être considéré comme une ressource opérationnelle.

Une machine peut avoir suffisamment d'espace aujourd'hui et devenir inutilisable
demain à cause de : journaux ; sauvegardes ; fichiers temporaires ; images de
conteneurs ; caches ; données applicatives.

Un professionnel doit donc savoir répondre à :

- Qu'est-ce qui consomme l'espace ?
- Quelle partie peut croître ?
- Quelle partie est temporaire ?
- Qu'est-ce qui doit être conservé ?
- Quelle est la politique de rétention ?
- Comment vérifier que la sauvegarde n'a pas elle-même saturé le système ?

La sauvegarde ne doit jamais être pensée séparément de la capacité de stockage.

---

## 11. Sauvegarder dans un environnement contraint

Une sauvegarde utile doit pouvoir être retrouvée et exploitée.

La question essentielle n'est donc pas seulement :

> « La sauvegarde existe-t-elle ? »

mais :

> « Puis-je récupérer les données dont j'ai besoin ? »

Une stratégie de sauvegarde doit être étudiée selon : les données concernées ; la
destination ; la fréquence ; la rétention ; l'intégrité ; la capacité disponible ;
le scénario de restauration ; la documentation.

Le référentiel de formation fournit notamment un exercice consacré à la sauvegarde.

Cet exercice doit être traité comme une pratique à réaliser et à vérifier, et non
comme une compétence automatiquement acquise parce qu'il figure dans le parcours.

---

## 12. Tester la restauration

Une sauvegarde non restaurée reste une hypothèse opérationnelle.

Le test de restauration permet de vérifier au minimum :

1. que la sauvegarde est accessible ;
2. que le format est exploitable ;
3. que les données attendues sont présentes ;
4. que la procédure de récupération est connue ;
5. que le résultat obtenu correspond au besoin.

La preuve produite doit distinguer :

```
sauvegarde configurée  ≠  sauvegarde exécutée  ≠  sauvegarde vérifiée
                     ≠  restauration réalisée  ≠  restauration réussie
```

Ces états ne sont pas équivalents.

---

## 13. Le réseau local comme laboratoire

Un réseau isolé peut devenir un laboratoire complet.

Il permet de pratiquer : adressage ; interfaces ; routes ; DNS ; services ; ports ;
filtrage ; VLAN ; VPN ; diagnostic de connectivité.

L'absence d'Internet n'empêche donc pas nécessairement l'apprentissage réseau.

Elle peut au contraire obliger à mieux comprendre les mécanismes locaux.

### Exercice

Construire un scénario minimal comportant : une machine cliente ; un service ; une
adresse IP ; un port ; éventuellement une résolution de nom locale.

Puis vérifier successivement :

```
interface → adresse → route → résolution → port → protocole → application
```

Chaque étape doit être observable.

---

## 14. Les ressources limitées imposent des arbitrages

Dans un environnement contraint, plusieurs solutions peuvent être techniquement
possibles.

Il faut alors comparer : coût en ressources ; complexité ; dépendances ; facilité
de diagnostic ; sécurité ; maintenance ; possibilité de récupération.

Le but n'est pas de choisir systématiquement la solution la plus légère.

Le but est de pouvoir **justifier le choix**.

Une solution professionnelle n'est pas seulement une solution qui fonctionne.

C'est une solution dont les contraintes et les compromis peuvent être expliqués.

---

## 15. Sécurité sous contrainte

La contrainte ne justifie pas l'abandon de la sécurité.

Elle peut cependant modifier les moyens disponibles.

Quelques principes restent fondamentaux : limiter les privilèges ; protéger les
secrets ; réduire les services exposés ; vérifier les ports ouverts ; documenter
les accès ; conserver les journaux utiles ; sauvegarder les configurations
importantes.

Un système isolé n'est pas automatiquement sécurisé.
Un système hors ligne n'est pas automatiquement sécurisé.
Un système disposant de peu de services n'est pas automatiquement sécurisé.

La sécurité doit être observée et vérifiée.

---

## 16. Documentation sous contrainte

Plus l'environnement est particulier, plus la documentation devient importante.

Une documentation utile doit permettre à une autre personne de comprendre : le
contexte ; les ressources ; l'architecture ; les dépendances ; les commandes
importantes ; les points de contrôle ; les procédures de récupération ; les limites
connues.

### À éviter

> « Installer X puis lancer Y. »

### À privilégier

> « X fournit telle fonction. Y dépend de X. Pour vérifier que X fonctionne,
> observer tel élément. Si ce contrôle échoue, examiner telle hypothèse. »

La documentation devient alors un outil de diagnostic.

---

## 17. L'environnement contraint comme exercice de sobriété

Une compétence importante de l'IT autodidacte consiste à savoir faire avec ce qui
existe déjà.

Cela implique de résister à plusieurs réflexes : installer immédiatement un nouvel
outil ; multiplier les dépendances ; remplacer un composant avant de comprendre le
problème ; chercher une solution externe avant d'examiner l'environnement local ;
modifier plusieurs paramètres simultanément.

La sobriété technique signifie ici :

> **introduire uniquement ce qui est nécessaire, après avoir établi pourquoi c'est
> nécessaire.**

---

## 18. Travailler lorsque l'information manque

Un environnement contraint peut aussi être un environnement mal documenté.

Dans ce cas, trois situations doivent être distinguées.

### Ce qui est observé

L'élément est directement vérifiable. Statut : **DÉMONTRÉ** lorsqu'une preuve
opérationnelle existe.

### Ce qui est déclaré

L'information provient d'une documentation, d'un historique ou d'une
déclaration. Statut : **DÉCLARÉ**.

### Ce qui reste inconnu

L'information ne peut pas encore être établie. Statut : **NON ÉTABLI**.

Dire « je ne sais pas encore » constitue une réponse professionnelle lorsqu'elle
est accompagnée d'une méthode pour obtenir l'information.

---

## 19. Ne pas confondre limitation et échec

Une contrainte peut empêcher une validation complète.

Cela ne signifie pas automatiquement que la compétence est absente.

> Le matériel disponible ne permet pas d'exécuter un modèle ou un service donné.

Ce constat établit une limitation expérimentale.

Il ne démontre ni que la solution est correcte, ni qu'elle est incorrecte.

Le bon résultat pédagogique peut alors être : identifier la contrainte ; mesurer
son impact ; documenter ce qui a pu être vérifié ; identifier ce qui reste non
établi ; définir la preuve qui serait nécessaire dans un environnement adapté.

---

## 20. Les environnements réels ne sont pas propres

Les dépôts et systèmes rencontrés dans la pratique peuvent contenir :
documentation obsolète ; fichiers temporaires ; dépendances non documentées ;
configurations incomplètes ; composants déclarés mais non vérifiés ; écarts entre
documentation et implémentation.

L'autodidacte doit apprendre à ne pas corriger automatiquement ce qu'il découvre.

La première question est :

> « Est-ce un défaut à corriger maintenant, ou un état à qualifier ? »

Cette distinction protège le système et améliore la qualité du diagnostic.

---

## 21. Le laboratoire de preuves

L'environnement contraint doit servir de laboratoire.

Pour chaque exercice, conserver trois moments.

### Avant

objectif ; environnement ; ressources ; hypothèses ; état initial.

### Pendant

commandes ; observations ; erreurs ; décisions ; changements effectués.

### Après

résultat ; vérification ; limites ; preuve produite ; documentation.

Cette méthode transforme une manipulation ponctuelle en expérience professionnelle
réutilisable.

---

## 22. Les exercices du parcours comme contraintes progressives

Le référentiel technique fournit déjà une progression pratique autour de tâches
telles que : navigation dans le système ; permissions ; répertoire partagé ;
service HTTP ; sauvegarde ; audit système ; Helm.

Ces exercices doivent être abordés comme des situations de pratique.

Leur présence dans le référentiel ne signifie pas que leur réalisation est
démontrée.

Pour chaque exercice, appliquer la chaîne :

```
ÉNONCÉ → RÉALISATION → VÉRIFICATION → PREUVE → STATUT
```

Un exercice non réalisé reste un exercice.

Un exercice réalisé sans vérification reste une pratique insuffisamment
qualifiée.

Un exercice vérifié mais non documenté produit une preuve difficilement
réutilisable.

---

## 23. Exercice — service local sans Internet

### Objectif

Mettre en œuvre un service local et démontrer son fonctionnement sans dépendre
d'Internet.

### Contraintes

environnement local ; ressources limitées ; aucune dépendance externe non
nécessaire ; vérification depuis la machine ou le réseau local.

### Travail

1. Décrire l'environnement.
2. Identifier les ressources disponibles.
3. Identifier les dépendances.
4. Installer ou utiliser le composant nécessaire.
5. Configurer le service.
6. Démarrer le service.
7. Vérifier le processus.
8. Vérifier l'écoute réseau.
9. Effectuer une requête réelle.
10. Documenter le résultat.
11. Identifier les limites.
12. Conserver la preuve.

### Preuves possibles

état du service ; écoute du port ; requête ; réponse ; journal ; capture de l'état
initial et final.

### Statut attendu

Ne pas remplir le statut avant réalisation.

---

## 24. Exercice — diagnostic avec ressources limitées

### Situation

Un service fonctionne lentement. Aucune cause n'est donnée.

### Travail

Ne pas commencer par modifier la configuration.

Établir successivement : charge CPU ; mémoire ; stockage ; processus ; état du
service ; réseau ; journaux ; évolution temporelle.

### Résultat attendu

Produire un court rapport : symptôme ; observations ; hypothèses ; vérifications ;
cause établie ou non établie ; action éventuelle ; résultat après action.

L'objectif n'est pas nécessairement de trouver une cause.

L'objectif est de démontrer une méthode de diagnostic.

---

## 25. Exercice — restauration en environnement isolé

### Objectif

Démontrer qu'une donnée sauvegardée peut être récupérée sans dépendre d'un
service externe.

### Travail

1. Définir la donnée.
2. Produire ou identifier la sauvegarde.
3. Vérifier sa présence.
4. Préparer un emplacement de restauration.
5. Restaurer.
6. Vérifier le contenu.
7. Comparer avec l'état attendu.
8. Documenter la procédure.
9. Identifier ce qui n'a pas pu être vérifié.

### Preuve

La preuve principale est le résultat de la restauration, pas seulement l'existence
du fichier de sauvegarde.

---

## 26. Exercice — réseau local isolé

### Objectif

Comprendre une chaîne réseau sans accès Internet.

### Travail

Construire un scénario local puis vérifier :

```
interface → adresse → route → résolution éventuelle → port → service → requête
```

Pour chaque étape, conserver : l'observation ; l'interprétation ; le statut.

L'exercice doit permettre de distinguer une absence de connectivité d'une panne
applicative.

---

## 27. Cahier de contraintes

Pour chaque laboratoire, utiliser le canevas suivant.

### Contexte

```
environnement      : ______________________
système            : ______________________
matériel           : ______________________
réseau             : ______________________
stockage           : ______________________
contraintes        : ______________________
```

### Objectif

```
résultat attendu   : ______________________
```

### Dépendances

```
dépendance 1       : ______________________
dépendance 2       : ______________________
dépendance 3       : ______________________
```

### Vérifications

```
contrôle 1         : ______________________
contrôle 2         : ______________________
contrôle 3         : ______________________
```

### Résultat

```
résultat obtenu    : ______________________
résultat non obtenu : ______________________
```

### Limites

```
élément non établi : ______________________
contrainte bloquante : ______________________
information manquante : ______________________
```

### Preuve

```
fichier            : ______________________
commande           : ______________________
sortie             : ______________________
capture            : ______________________
journal            : ______________________
```

### Statut

```
DÉMONTRÉ           : ______________________
DÉCLARÉ            : ______________________
INTERPRÉTÉ         : ______________________
OBJECTIF           : ______________________
NON ÉTABLI         : ______________________
```

---

## 28. Ce que l'environnement contraint doit apprendre

À la fin de cette partie, l'apprenant doit progressivement savoir : mesurer son
environnement ; identifier ses contraintes ; distinguer dépendance locale et
externe ; travailler avec peu de ressources ; diagnostiquer avant de modifier ;
vérifier un service au-delà de son simple démarrage ; sauvegarder et tester une
restauration ; raisonner sur un réseau isolé ; documenter un système particulier ;
reconnaître une information non établie ; justifier un choix technique ; produire
une preuve exploitable.

Ces capacités ne doivent pas être considérées comme acquises simplement parce que
le chapitre a été lu.

Elles deviennent des compétences professionnelles lorsqu'elles ont été
pratiquées, vérifiées et documentées.

---

## 29. Relation avec la matrice de preuves

La matrice de preuves permet de relier le travail réalisé à une compétence.

La chaîne reste :

```
SOURCE → PRATIQUE → OBSERVATION → VÉRIFICATION → PREUVE → STATUT
```

Un environnement contraint fournit surtout des occasions de produire des preuves.

Il ne fournit pas automatiquement ces preuves.

La matrice ne doit donc pas être remplie par anticipation.

| Situation | Statut |
|---|---|
| Un exercice prévu | **OBJECTIF** |
| Un résultat annoncé sans vérification | **DÉCLARÉ** |
| Une interprétation technique | **INTERPRÉTÉ** |
| Une compétence dont la preuve manque | **NON ÉTABLIE** |
| Une exécution vérifiée et documentée | **DÉMONTRÉ** |

---

## 30. Résultat attendu

Cette partie doit conduire l'autodidacte à changer de réflexe.

Au lieu de demander immédiatement :

> « Quel outil dois-je installer ? »

il doit apprendre à demander :

> « Quelles sont mes contraintes, quelles ressources sont disponibles, qu'est-ce que
> je peux observer et quelle preuve dois-je produire ? »

Au lieu de considérer l'absence d'Internet comme une impossibilité, il doit
apprendre à identifier ce qui peut fonctionner localement.

Au lieu de considérer une machine limitée comme un obstacle absolu, il doit
apprendre à mesurer la contrainte et à adapter la solution.

Au lieu de considérer une configuration comme une preuve, il doit vérifier le
comportement réel.

La compétence recherchée est donc moins :

> **savoir utiliser un outil**

que :

> **savoir produire un résultat vérifiable dans un environnement donné, en maîtrisant
> ses contraintes et en sachant expliquer les limites de ce qui a été démontré.**

---

## Synthèse

L'environnement contraint constitue un terrain privilégié pour former un IT
autodidacte.

Il oblige à :

```
observer → mesurer → raisonner → agir avec sobriété
        → vérifier → documenter → produire une preuve
```

La contrainte n'est pas l'ennemie de l'apprentissage.

Elle permet de rendre visibles les dépendances, les hypothèses, les limites et
les méthodes de diagnostic.

Mais une contrainte ne doit jamais être utilisée pour masquer une absence de
preuve.

Le professionnel doit pouvoir dire précisément : ce qu'il a fait ; ce qu'il a
observé ; ce qu'il a vérifié ; ce qu'il en déduit ; ce qu'il n'a pas pu établir ;
et quelle preuve serait nécessaire pour aller plus loin.

C'est cette discipline qui transforme une expérience réalisée dans un
environnement imparfait en compétence professionnelle lisible.

---

## Ce que devient le cahier de contraintes

Le cahier de la section 27 n'est pas un exercice de plus. C'est **la matière
première de la partie suivante**, et il faut comprendre pourquoi avant de
continuer.

### Pourquoi la fiche de preuve reprend les mêmes champs

Vous allez constater, en arrivant à la Partie IV, que la fiche de preuve contient
des champs que vous venez déjà de remplir : *environnement*, *système*,
*matériel*, *résultat attendu*, *résultat obtenu*, *journal*, *sortie*, et les
cinq statuts.

**Ce n'est pas une duplication accidentelle.** Les deux canevas occupent deux
étages différents du même travail.

```
CONTRAINTE          ce que l'environnement impose
        ↓
OBSERVATION         ce que j'ai réellement constaté
        ↓
RÉSULTAT            ce que j'ai obtenu, ou non
        ↓
QUALIFICATION       quel statut : DÉMONTRÉ / DÉCLARÉ / INTERPRÉTÉ / OBJECTIF / NON ÉTABLI
        ↓
PREUVE              l'artefact qui permet à un tiers de le vérifier
        ↓
FORMULATION         ce que je peux en dire, sans exagérer
```

Le **cahier de contraintes** (Partie III) s'arrête à l'étape *qualification*. Il
constate : voici mon environnement, voici ce que j'ai vu, voici ce que cela
permet de dire.

La **fiche de preuve** (Partie IV) reprend ces mêmes constatations et leur ajoute
ce qui manquait pour qu'un tiers puisse les vérifier : la commande exacte, la
sortie conservée, le test, et la limite explicite de ce qui n'a pas été couvert.

Autrement dit : **la Partie IV ne demande pas de recommencer. Elle demande de
transformer des observations en preuves vérifiables.** Les 13 champs communs sont
déjà remplis — la Partie IV vous fait y ajouter les 13 autres.

### Ce qui change concrètement

À la fin de la Partie III, vous savez travailler dans un environnement imparfait
et dire ce que vous y avez observé.

À la fin de la Partie IV, vous saurez **le prouver à quelqu'un d'autre**.

C'est la différence entre un constat et une preuve. Un constat est vrai pour
vous ; une preuve est vérifiable par un tiers, ce qui suppose qu'elle soit
conservée, datée et contextualisée — et qu'elle indique aussi ce qu'elle ne
couvre pas.

La partie suivante passe de la preuve à sa mise en discours : non pas
expliquer une expérience imaginée, mais expliquer celle que vous venez
d'établir.