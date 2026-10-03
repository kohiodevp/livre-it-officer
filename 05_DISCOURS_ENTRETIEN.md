# 05 — Expliquer et défendre son travail

**Partie V — EXPLIQUER ET DÉFENDRE SON TRAVAIL**

Cette partie prolonge la production de preuves. Elle ne transforme pas le livre en
guide d'entretien : l'entretien est **une** situation d'expression parmi
d'autres — documentation, revue par les pairs, passation, intervention, dialogue
technique.

---

## Introduction — Une compétence professionnelle doit pouvoir être expliquée

Un IT autodidacte peut savoir faire beaucoup de choses sans disposer encore du
vocabulaire professionnel permettant de les présenter clairement.

Il peut avoir installé un service, diagnostiqué une panne, écrit un script,
construit une configuration ou travaillé dans un environnement contraint.
Pourtant, lorsqu'on lui demande :

- « Qu'avez-vous réellement fait ? »
- « Comment savez-vous que cela fonctionne ? »
- « Pourquoi avez-vous choisi cette solution ? »
- « Qu'est-ce qui a échoué ? »
- « Quelle était votre limite ? »
- « Comment transmettriez-vous ce travail à quelqu'un d'autre ? »

il peut répondre par une liste d'outils plutôt que par une description
professionnelle de son travail.

Cette partie travaille précisément ce passage :

```
pratique → compétence structurée → preuve → explication → transmission
```

L'objectif n'est pas d'apprendre à donner une réponse qui paraît professionnelle.

L'objectif est de pouvoir **décrire fidèlement ce qui a été fait, ce qui a été
vérifié, ce qui reste à établir et pourquoi les choix ont été faits**.

---

## 1. Expliquer n'est pas embellir

Une présentation professionnelle ne consiste pas à rendre un projet plus
impressionnant que ce que les preuves permettent d'établir.

Elle consiste à réduire l'écart entre : ce qui a réellement été fait ; ce qui peut
être démontré ; ce qui peut être expliqué ; ce qui reste à apprendre.

Une formulation professionnelle peut donc contenir une limite.

> « J'ai préparé la configuration et vérifié sa structure, mais je n'ai pas encore
> validé son déploiement complet. »

Cette phrase est plus exploitable qu'une affirmation générale comme :

> « Je maîtrise le déploiement de cette infrastructure. »

La première distingue l'action réalisée de la compétence qui reste à démontrer.

---

## 2. Les cinq statuts restent applicables à l'oral

Le discours professionnel doit respecter les mêmes statuts que la matrice de
preuves.

| Statut | Signification |
|---|---|
| **DÉMONTRÉ** | une preuve issue d'une exécution constatée permet d'établir le résultat |
| **DÉCLARÉ** | l'information est affirmée mais la preuve disponible ne permet pas de l'établir |
| **INTERPRÉTÉ** | il s'agit d'une lecture ou d'une déduction à partir d'éléments observés |
| **OBJECTIF** | compétence ou pratique que l'on prévoit encore de développer |
| **NON ÉTABLI** | les éléments disponibles ne permettent pas de conclure |

Ces statuts ne sont pas des formulations à réciter pendant un entretien.

Ils servent à construire un discours exact.

---

## 3. Répondre à partir des faits

Une réponse technique solide peut suivre quatre mouvements simples :

1. **contexte** ;
2. **action** ;
3. **vérification** ;
4. **limite ou résultat**.

### Exemple générique

> « Le problème concernait un service qui devait être accessible localement. J'ai
> commencé par vérifier l'état du processus et le port d'écoute. J'ai ensuite testé
> la réponse du service avec un outil adapté. La vérification a permis d'établir que
> le service répondait correctement dans cet environnement. Je n'ai pas vérifié son
> comportement après redémarrage de la machine. »

Cette réponse est plus informative qu'une succession de noms de logiciels.

---

## 4. La question « qu'avez-vous fait ? »

Cette question demande une action, pas une définition théorique.

### À éviter

> « Docker permet de faire fonctionner des conteneurs. »

### À privilégier

> « J'ai utilisé Docker Compose pour décrire plusieurs services et leurs
> dépendances. J'ai ensuite vérifié la configuration générée avant de procéder aux
> étapes d'exécution autorisées. »

La réponse doit permettre de distinguer :

```
connaissance → utilisation → vérification → maîtrise reproductible
```

---

## 5. La question « comment avez-vous vérifié ? »

C'est souvent la question qui transforme une déclaration en preuve.

Une bonne réponse identifie : ce qui devait être vrai ; le test utilisé ; le
résultat observé ; la conclusion autorisée.

```
Attendu → test → observation → conclusion
```

### Exemple

> « Le service devait accepter les connexions sur son port prévu. J'ai donc vérifié
> le port d'écoute puis effectué une requête locale. Le port était ouvert et la
> requête obtenait la réponse attendue. Je peux donc établir le fonctionnement dans
> le périmètre testé. »

La dernière phrase doit rester proportionnée au test.

Un test local ne démontre pas automatiquement le fonctionnement en production.

---

## 6. La question « pourquoi avez-vous choisi cette solution ? »

Une justification technique doit partir de contraintes réelles.

```
Contrainte → besoin → choix → compromis
```

### Exemple

> « L'environnement devait fonctionner sans accès Internet permanent. J'ai donc
> privilégié une architecture qui limite les dépendances externes. Le compromis est
> que les mises à jour et la récupération de nouvelles dépendances doivent être
> préparées séparément. »

Une décision professionnelle n'est pas nécessairement une décision parfaite.

Elle doit être explicable au regard du contexte.

---

## 7. La question « qu'est-ce qui n'a pas fonctionné ? »

Un incident n'est pas automatiquement un échec professionnel.

Il devient une occasion d'apprentissage lorsque l'on sait distinguer : le
symptôme ; l'hypothèse ; le diagnostic ; l'action ; la vérification ; la limite
restante.

```
État initial → symptôme → hypothèses → diagnostic
            → action → vérification → résultat
```

Ne pas supprimer l'échec de la présentation pour rendre le récit plus propre.

Un problème documenté peut constituer une preuve de méthode de diagnostic.

---

## 8. Décrire un diagnostic sans inventer la cause

Une erreur fréquente consiste à transformer une hypothèse en cause certaine.

### Exemple incorrect

> « Le service ne fonctionnait pas parce que le réseau était mal configuré. »

Si le réseau n'a pas été vérifié, cette phrase dépasse les preuves.

### Formulation correcte

> « Le service ne répondait pas. La configuration réseau faisait partie des
> hypothèses étudiées, mais la cause n'a pas été établie dans le périmètre du
> test. »

La précision n'affaiblit pas le discours.

Elle montre que l'on sait distinguer observation et interprétation.

---

## 9. Expliquer une architecture

Une architecture doit pouvoir être expliquée à plusieurs niveaux.

| Niveau | Question |
|---|---|
| **1 — Vue métier** | Que permet le système ? |
| **2 — Vue fonctionnelle** | Quels sont les principaux flux ? |
| **3 — Vue technique** | Quels services, composants et dépendances sont utilisés ? |
| **4 — Vue opérationnelle** | Comment le système est-il démarré, surveillé, sauvegardé et dépanné ? |

Une bonne présentation peut donc commencer simplement :

> « Le système collecte une information, la traite localement puis la transmet
> lorsqu'une connexion est disponible. »

Puis descendre progressivement vers les composants techniques.

---

## 10. Le dessin d'architecture comme outil de communication

Un schéma n'est pas uniquement un livrable technique.

C'est également un outil pour expliquer son raisonnement.

Pour présenter un schéma :

1. commencer par le point d'entrée ;
2. suivre le flux principal ;
3. identifier les composants ;
4. expliquer les dépendances ;
5. signaler les points de défaillance importants ;
6. préciser les éléments réellement vérifiés.

Ne pas commencer par une longue description de chaque technologie.

Commencer par le fonctionnement global.

---

## 11. Montrer un artefact

Une démonstration technique doit répondre à une question précise.

Avant de montrer un fichier, une commande ou une interface, déterminer :

> **Qu'est-ce que cet artefact doit démontrer ?**

| Artefact | Question possible |
|---|---|
| configuration | la configuration déclarée est-elle correcte ? |
| script | le comportement attendu est-il implémenté ? |
| journal | qu'est-il réellement arrivé ? |
| commande | quel état peut-elle établir ? |
| résultat de test | quel comportement a été vérifié ? |
| schéma | quelle architecture est proposée ou observée ? |

Un fichier de configuration n'est pas automatiquement une preuve d'exécution.

Un journal n'est pas automatiquement une preuve que le système fonctionne
aujourd'hui.

Une capture d'écran n'est pas automatiquement une preuve reproductible.

---

## 12. La démonstration courte

Pour une présentation courte, utiliser une séquence stable :

1. **objectif** ;
2. **contexte** ;
3. **artefact** ;
4. **action ou test** ;
5. **résultat** ;
6. **limite**.

### Exemple

> « L'objectif était de vérifier que le service répondait localement. Voici sa
> configuration. Je vérifie ensuite le processus et le port d'écoute, puis j'effectue
> la requête. Le résultat attendu est obtenu. Cette démonstration couvre le
> fonctionnement local ; elle ne couvre pas encore le comportement après
> redémarrage. »

Cette structure évite la démonstration improvisée.

---

## 13. Décrire un projet sans réciter sa documentation

Une présentation professionnelle ne doit pas être la lecture du README.

Elle doit répondre à cinq questions : quel problème ; quelles contraintes ; quelle
solution ; quelles vérifications ; quelles limites.

Formule courte :

```
Problème → contraintes → choix → preuve → limite
```

Cette structure permet de transformer un projet en expérience professionnelle
compréhensible.

---

## 14. Transformer une tâche en compétence

Dire :

> « J'ai écrit un script Bash. »

décrit une action.

Dire :

> « J'ai automatisé une tâche d'administration avec un script Bash, en contrôlant
> les erreurs et les dépendances nécessaires. »

décrit davantage la compétence.

Mais la formulation doit rester proportionnée aux preuves disponibles.

Si le script n'a pas été exécuté dans un environnement réel, ne pas présenter son
existence comme une preuve d'exploitation opérationnelle.

La chaîne reste :

```
action → vérification → preuve → formulation
```

---

## 15. STAR+ adapté aux situations techniques

La structure STAR peut être utile, à condition de l'adapter à la réalité
technique.

| Temps | Contenu |
|---|---|
| **S — Situation** | contexte |
| **T — Tâche** | objectif |
| **A — Action** | ce qui a été fait |
| **R — Résultat** | ce qui a été obtenu et vérifié |
| **+ — Limite** | ce qui n'a pas été établi ou ce qui reste à améliorer |

Le « + » est essentiel.

Il empêche le récit de transformer automatiquement toute expérience en réussite
complète.

### Canevas

```
Situation         : ______________________
Tâche             : ______________________
Action            : ______________________
Résultat vérifié  : ______________________
Limite            : ______________________
Ce que j'en ai appris : __________________
```

Ce canevas doit rester vide tant que l'apprenant ne possède pas les éléments
nécessaires.

---

## 16. Raconter un incident technique

Un récit d'incident doit être chronologique et vérifiable.

### Canevas

**1. État initial** — qu'est-ce qui fonctionnait ou était attendu ?

**2. Symptôme** — qu'est-ce qui a été observé ?

**3. Hypothèses** — quelles causes possibles ont été envisagées ?

**4. Diagnostic** — quels tests ont permis d'éliminer ou de confirmer certaines
hypothèses ?

**5. Action** — quelle modification ou intervention a été effectuée ?

**6. Vérification** — quel test a permis de contrôler le résultat ?

**7. Limite** — qu'est-ce qui reste non établi ?

Cette structure permet de montrer une méthode plutôt qu'une simple anecdote.

---

## 17. Parler d'une erreur

Une erreur peut être présentée professionnellement sans être masquée.

Il faut pouvoir répondre à quatre questions : qu'ai-je fait ; pourquoi cela
posait-il problème ; comment l'ai-je détecté ; qu'est-ce que je ferai
différemment.

Une erreur documentée vaut mieux qu'une erreur dissimulée.

Elle devient particulièrement instructive lorsqu'elle conduit à une règle de
travail reproductible.

---

## 18. Ce que signifie « je ne sais pas »

Un professionnel n'est pas obligé de connaître immédiatement toutes les réponses.

Il doit savoir délimiter ce qu'il sait.

### Formulations utiles

> « Je ne peux pas l'établir avec les éléments dont je dispose. »

> « Je connais le principe, mais je n'ai pas encore réalisé cette opération. »

> « Je l'ai testé dans cet environnement, mais pas dans cette autre
> configuration. »

> « Je commencerais par vérifier X avant de conclure. »

Ces réponses sont plus précises qu'une réponse improvisée.

---

## 19. Défendre un choix technique

Défendre une solution ne signifie pas prétendre qu'elle est universellement
meilleure.

Une décision technique dépend : du contexte ; des ressources ; des contraintes ;
du niveau de risque ; des compétences disponibles ; de la maintenabilité recherchée.

La formulation professionnelle devient :

> « Dans ce contexte, j'ai choisi X parce que… »

plutôt que :

> « X est toujours la meilleure solution. »

Cette différence est fondamentale.

---

## 20. Présenter un compromis

Tout choix technique peut comporter un compromis.

| Élément | Réponse |
|---|---|
| Besoin | |
| Contraintes | |
| Solution retenue | |
| Avantage recherché | |
| Coût ou inconvénient | |
| Risque accepté | |
| Mesure de réduction du risque | |
| Preuve disponible | |

L'apprenant doit pouvoir expliquer non seulement ce qu'il a choisi, mais également
ce qu'il a accepté en choisissant cette solution.

---

## 21. La documentation comme prolongement du discours

Expliquer oralement et documenter poursuivent le même objectif :

> rendre le travail compréhensible par une autre personne.

Une documentation opérationnelle doit permettre à un tiers de comprendre : le
contexte ; l'état attendu ; les prérequis ; les actions ; les vérifications ; les
erreurs connues ; les limites ; le point de reprise.

Une documentation qui ne permet qu'à son auteur de se souvenir de ce qu'il a fait
reste insuffisante pour une passation.

---

## 22. La revue par les pairs

Présenter son travail à un autre IT permet de tester sa compréhension.

La revue peut porter sur : la cohérence ; la sécurité ; la reproductibilité ; les
dépendances ; les hypothèses ; les tests ; la documentation.

L'objectif n'est pas de défendre son code à tout prix.

L'objectif est de pouvoir répondre :

> « Qu'est-ce qui vous permet d'affirmer cela ? »

Une remarque de revue devient alors une nouvelle occasion de vérifier ou de
documenter.

---

## 23. La passation

Un travail professionnel doit pouvoir être transmis.

Pour une passation, fournir au minimum : objectif ; architecture ; prérequis ;
procédure ; vérifications ; points de surveillance ; sauvegarde et restauration
si concernées ; incidents connus ; limites ; point de contact ou procédure
d'escalade lorsqu'elle existe.

La passation constitue un test pratique de la qualité de la documentation.

Si personne d'autre ne peut reprendre le travail, sa reproductibilité doit être
réexaminée.

---

## 24. Les questions techniques à préparer

Une préparation utile ne consiste pas à mémoriser des réponses toutes faites.

Pour chaque compétence, préparer plutôt cinq questions.

### Comprendre

> Qu'est-ce que cette technologie ou cette méthode permet de faire ?

### Pratiquer

> Qu'ai-je réellement manipulé ?

### Vérifier

> Comment ai-je vérifié le résultat ?

### Expliquer

> Comment présenterais-je mon intervention en quelques phrases ?

### Limiter

> Qu'est-ce que je n'ai pas encore démontré ?

Cette série transforme la préparation en travail technique.

---

## 25. Questions de défense technique

Pour chaque projet, l'apprenant doit pouvoir travailler les questions suivantes :

1. Quel problème cherchiez-vous à résoudre ?
2. Quelles étaient les contraintes ?
3. Pourquoi cette architecture ?
4. Quel était votre rôle exact ?
5. Quelle partie avez-vous réellement réalisée ?
6. Comment avez-vous vérifié le résultat ?
7. Quel incident avez-vous rencontré ?
8. Comment avez-vous établi sa cause ?
9. Qu'est-ce qui n'a pas été testé ?
10. Que feriez-vous avant une mise en production ?

Ces questions ne sont pas un questionnaire à apprendre par cœur.

Elles constituent une grille d'auto-évaluation.

---

## 26. Préparer une démonstration technique

Avant toute démonstration, remplir :

| Élément | Réponse |
|---|---|
| Objectif | |
| Périmètre | |
| État initial | |
| Préconditions | |
| Action | |
| Vérification | |
| Résultat attendu | |
| Résultat observé | |
| Limites | |
| Preuve conservée | |

Une démonstration qui ne possède pas de critère de réussite précis risque de
devenir une simple présentation visuelle.

---

## 27. Les quatre projets du laboratoire comme exercices de discours

Les projets du laboratoire peuvent servir à entraîner cette méthode, mais leurs
niveaux de preuve restent différents.

### `pi-kiosk-offline`

L'apprenant peut expliquer l'architecture documentée et identifier la dépendance
autour du service attendu sur `127.0.0.1:8080`.

Il ne doit pas présenter comme démontré le fonctionnement complet du kiosque si la
preuve d'exécution correspondante n'existe pas.

### `infra-as-code`

L'apprenant peut présenter les services Compose, les réseaux et les rôles Ansible
observés.

Il doit distinguer cette configuration de la preuve d'un déploiement complet et
reproductible.

### `scripts-admin`

L'apprenant peut présenter la structure des scripts, leurs conventions et leurs
dépendances observées.

La présence des scripts ne constitue pas, à elle seule, une preuve de leur
exécution opérationnelle.

### `geo-android-offline`

L'apprenant peut expliquer la structure Python, la configuration Gradle/Chaquopy et
les composants prévus.

Il doit cependant distinguer ces éléments de la preuve d'un APK construit et
fonctionnel.

Ces quatre exemples enseignent la même règle :

> **Présenter précisément ce que l'artefact permet d'établir, pas davantage.**

---

## 28. Le discours professionnel et la matrice de preuves

La matrice ne sert pas seulement à préparer une candidature.

Elle permet de contrôler le discours.

```
COMPÉTENCE → PRATIQUE → VÉRIFICATION → PREUVE → STATUT → FORMULATION
```

| Compétence | Preuve | Statut | Formulation |
|---|---|---|---|
| Docker/Compose | configuration observée | DÉCLARÉ ou NON ÉTABLI selon périmètre | « J'ai travaillé sur une configuration Compose… » |
| Script Bash | script présent et analysé | DÉCLARÉ / NON ÉTABLI pour l'exécution | « J'ai développé un script… » |
| Diagnostic | test exécuté et résultat conservé | DÉMONTRÉ | « J'ai diagnostiqué… et vérifié… » |
| Domaine non pratiqué | aucune preuve | OBJECTIF | « Je souhaite encore développer cette compétence. » |

Le statut exact dépend toujours de la preuve réellement disponible.

---

## 29. Ne pas confondre confiance et preuve

Une personne peut être très sûre d'elle et disposer de peu de preuves.

Une autre peut avoir beaucoup pratiqué mais présenter son expérience avec
hésitation.

Le travail du livre consiste à rapprocher les deux dimensions :

```
confiance fondée sur la pratique vérifiée
```

La preuve ne remplace pas la confiance.

Elle donne à la confiance une base vérifiable.

---

## 30. Construire son vocabulaire professionnel

Remplacer progressivement les formulations vagues.

| Formulation vague | Formulation plus précise |
|---|---|
| « Ça marche. » | « Le test X produit le résultat attendu. » |
| « J'ai fait du Docker. » | « J'ai utilisé Docker Compose pour… » |
| « J'ai sécurisé le serveur. » | « J'ai appliqué et vérifié les mesures suivantes… » |
| « Le réseau était cassé. » | « Le test X a montré que… » |
| « Tout est prêt. » | « Les éléments suivants sont vérifiés ; les éléments suivants restent à établir. » |
| « Je maîtrise. » | « Je peux démontrer que je sais réaliser… dans ce périmètre. » |

Le vocabulaire professionnel commence par la précision.

---

## 31. Répondre quand la question dépasse la preuve

Une question peut porter sur un élément que l'apprenant n'a jamais testé.

Il ne faut pas inventer une expérience.

```
« Je connais le principe. En revanche, je n'ai pas encore réalisé cette opération
dans un environnement que je peux présenter comme preuve. Pour la traiter, je
commencerais par… »
```

Cette réponse permet de montrer : ce qui est connu ; ce qui a été pratiqué ; ce
qui reste à pratiquer ; la méthode envisagée.

---

## 32. Répondre à une objection

Lorsqu'une personne conteste un choix, éviter de défendre immédiatement la
solution.

Commencer par identifier l'objection :

> « Vous soulevez le risque de… »

Puis distinguer : fait ; hypothèse ; choix ; compromis ; preuve.

### Exemple de structure

> « Le fait établi est X. Mon choix était Y pour la contrainte Z. Le compromis est A.
> La vérification que j'ai réalisée couvre B, mais pas encore C. »

Cette méthode permet de discuter techniquement sans transformer la discussion en
confrontation personnelle.

---

## 33. L'entretien comme exercice de vérité technique

L'entretien devient alors une situation particulière d'un principe plus général :

> **être capable d'expliquer son travail à quelqu'un qui n'était pas présent
> lorsqu'il a été réalisé.**

La même compétence est utile pour : un collègue ; un responsable ; un client ; un
auditeur ; un membre de l'équipe ; une personne qui reprend le système.

L'entretien n'est donc pas la finalité de la compétence.

Il constitue l'une de ses situations d'expression.

---

## 34. Préparer son récit professionnel

Le récit doit rester factuel.

### Canevas

**Mon point de départ**

> …

**Ce que j'ai appris par la pratique**

> …

**Les environnements dans lesquels j'ai travaillé**

> …

**Les compétences que je peux actuellement démontrer**

> …

**Les compétences encore en développement**

> …

**La valeur que je peux apporter**

> …

Ce récit ne doit pas transformer un objectif en expérience acquise.

---

## 35. Le passage de l'expérience à la valeur

La valeur professionnelle ne vient pas uniquement de la technologie utilisée.

Elle peut venir de la capacité à : diagnostiquer ; automatiser ; documenter ;
sécuriser ; vérifier ; réduire une dépendance ; travailler sous contrainte ;
transmettre ; apprendre de manière autonome.

L'expérience devient lisible lorsqu'elle est reliée à une compétence observable.

---

## 36. Exercice — Une minute pour expliquer un travail

Choisir une réalisation réelle.

En une minute, répondre à : quel était le problème ; qu'avez-vous fait ; comment
l'avez-vous vérifié ; quel résultat avez-vous obtenu ; quelle limite subsiste.

Enregistrer ou écrire la réponse.

Puis vérifier : ai-je parlé de faits ; ai-je cité une vérification ; ai-je confondu
intention et résultat ; ai-je indiqué ma limite ; pourrais-je montrer la preuve
correspondante.

---

## 37. Exercice — Défendre une décision

Choisir une décision technique réellement prise.

```
Contexte         : ______________________
Besoin           : ______________________
Contraintes      : ______________________
Options envisagées: _____________________
Choix            : ______________________
Raison           : ______________________
Compromis        : ______________________
Vérification     : ______________________
Limite           : ______________________
```

La réponse doit rester compréhensible par un professionnel qui ne connaît pas le
projet.

---

## 38. Exercice — Présenter une erreur

Choisir une erreur réellement rencontrée.

Décrire :

```
OBSERVATION → HYPOTHÈSE → TEST → RÉSULTAT
           → CORRECTION → VÉRIFICATION → LEÇON
```

Si la cause n'a pas été établie, l'écrire explicitement.

Le but n'est pas de fabriquer une histoire intéressante.

Le but est de montrer une méthode de travail.

---

## 39. Exercice final — La défense complète

Choisir une compétence figurant dans la matrice.

Construire une présentation de cinq minutes.

### Minute 1 — Contexte

Présenter le problème et les contraintes.

### Minute 2 — Intervention

Décrire précisément son rôle et ses actions.

### Minute 3 — Vérification

Présenter les tests et les résultats.

### Minute 4 — Limites

Identifier ce qui n'a pas été démontré.

### Minute 5 — Recul professionnel

Expliquer ce qui pourrait être amélioré ou approfondi.

Puis répondre aux questions : Pourquoi ? Comment savez-vous ? Qu'avez-vous testé ?
Qu'est-ce qui a échoué ? Que feriez-vous autrement ? Qu'est-ce qui reste à
démontrer ?

---

## 40. Critères de réussite

La partie est réussie lorsque l'apprenant peut :

1. expliquer une réalisation sans exagérer son rôle ;
2. distinguer action, résultat et preuve ;
3. justifier un choix par le contexte et les contraintes ;
4. décrire un incident sans inventer sa cause ;
5. reconnaître une limite sans transformer cette limite en échec global ;
6. présenter un artefact en indiquant ce qu'il démontre ;
7. documenter un travail pour qu'un tiers puisse le comprendre ;
8. répondre à une objection en revenant aux faits ;
9. transformer une expérience en compétence lisible ;
10. adapter son discours à la personne qui l'écoute.

---

## Synthèse — Expliquer ce que l'on sait réellement faire

L'IT autodidacte ne doit pas choisir entre deux extrêmes : minimiser systématiquement
son expérience ; exagérer ce qu'il peut démontrer.

La démarche professionnelle se situe entre les deux.

Elle consiste à dire :

- **ce que j'ai fait,**
- **ce que j'ai vérifié,**
- **ce que les preuves établissent,**
- **ce qui reste limité,**
- **et ce que je dois encore apprendre.**

La préparation à l'entretien devient alors une conséquence naturelle du travail
effectué.

La même méthode sert à expliquer un projet, rédiger une documentation, participer
à une revue, effectuer une passation ou défendre une décision technique.

La boucle complète du livre se poursuit :

```
COMPRENDRE → PRATIQUER → VÉRIFIER → PRODUIRE UNE PREUVE
           → EXPLIQUER → IDENTIFIER UNE LIMITE
           → (progression)
```

Une compétence professionnelle n'est donc pas seulement quelque chose que l'on
sait faire.

C'est quelque chose que l'on peut **faire, vérifier, expliquer, transmettre et
situer honnêtement dans ses limites**.

La Partie V est ainsi volontairement **professionnalisation et communication**, et
non un basculement vers un « manuel d'entretien ». Les lacunes de `prep_entretien/`
restent des lacunes : elles ne sont pas transformées en compétences ou en preuves
acquises.