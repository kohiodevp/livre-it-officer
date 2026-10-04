# 00 — Positionnement

Mode d'emploi du livre.

Ce fichier ne contient aucune notion technique. Il explique **comment lire et
utiliser l'ouvrage**, et fixe les conventions qui rendent chaque chapitre
interprétable de la même manière.

---

## 1. À qui s'adresse ce livre

Ce livre s'adresse à un informaticien **autodidacte** qui pratique, mais dont
la compétence reste difficile à démontrer — parce qu'elle n'a pas été organisée
en preuves, ou parce que les preuves produites ne sont pas visibles.

Il ne suppose pas de diplôme en informatique. Il suppose de l'expérience réelle :
des machines administrées, des pannes diagnostiquées, des commandes exécutées,
des décisions prises sans documentation.

### Cap éditorial

> **Former un IT autodidacte à transformer sa pratique en compétences
> structurées, vérifiables et professionnelles.**

Le livre n'est pas un manuel de préparation à un entretien professionnel.
L'entretien est **un usage parmi d'autres** des compétences développées ici, et
non leur finalité.

Les formules normatives du livre sont regroupées dans l'annexe
`annexes/PHRASE_MANIFESTE.md` : elles fixent le cadre de lecture et de rigueur,
sans se substituer à la méthode elle-même.

---

## 2. La boucle pédagogique

Chaque notion du livre suit six temps. Cette boucle est le fil conducteur de
l'ouvrage.

```
        COMPRENDRE
             ↓
        PRATIQUER
             ↓
         VÉRIFIER
             ↓
      PRODUIRE UNE PREUVE
             ↓
         EXPLIQUER
             ↓
    IDENTIFIER UNE LIMITE
             ↓
        (progression)
```

| Temps | Ce qui est attendu |
|---|---|
| **Comprendre** | Savoir dire ce que le système fait, et pourquoi il le fait ainsi |
| **Pratiquer** | Réaliser la tâche soi-même, sur un environnement maîtrisé |
| **Vérifier** | Contrôler le résultat par une commande, une mesure, un test |
| **Produire une preuve** | Conserver un artefact reproductible : configuration, sortie, dépôt, compte rendu |
| **Expliquer** | Présenter son travail : à un recruteur, un collègue, un auditeur |
| **Identifier une limite** | Nommer ce qui n'est pas maîtrisé et orienter la suite |

### Le sixième temps n'est pas un échec

**Identifier une limite** ne valide pas un manque à masquer. C'est une étape de
travail au même titre que les cinq autres.

Elle sert à :

- rendre visible ce qui reste non maîtrisé, au lieu de le laisser supposer ;
- éviter qu'une affirmation non vérifiée soit présentée comme une compétence ;
- donner une direction concrète à la progression suivante.

Une page qui décrit ce qui fonctionne **et** ce qui reste à prouver vaut mieux
qu'une page qui ne décrit que la réussite.

---

## 3. Les statuts

Deux jeux de statuts cohabitent dans l'ouvrage. Ils ne disent pas la même chose
et ne doivent pas être confondus.

### 3.1 Statuts de preuve — ce que l'on peut affirmer

Ils qualifient **un contenu**. On les rencontre dans les chapitres et dans la
matrice des preuves.

| Statut | Signification |
|---|---|
| **DÉMONTRÉ** | Une preuve vérifiable, issue d'une exécution constatée, établit le résultat ou la compétence dans le périmètre considéré. Un artefact non exécuté n'atteint jamais ce statut : il reste DÉCLARÉ. |
| **DÉCLARÉ** | La documentation affirme ; l'exécution n'a pas été observée |
| **INTERPRÉTÉ** | Une déduction à partir de plusieurs observations |
| **OBJECTIF** | Pas d'artefact ; c'est une cible d'apprentissage |
| **NON ÉTABLI** | Une affirmation existe mais n'a pas pu être vérifiée |

**Règle** : un artefact n'est pas automatiquement une preuve de compétence.
Un fichier existe ; ce qu'il démontre dépend de ce qui a été exécuté, observé
ou mesuré.

### 3.2 Marqueurs de travail — où en est la rédaction

Ils indiquent **l'état d'avancement d'un chapitre** et ne sont pas des jugements
de valeur.

| Marqueur | Signification |
|---|---|
| **OBS** | Contenu observé et vérifiable en l'état |
| **DÉD** | Contenu déduit, paragraphe ou cas de figure |
| **N.D.** | Information non disponible — à produire |
| **BLOQUÉ** | Contenu dépendant d'une preuve ou d'une décision externe |
| **ÉCHEC** | Contenu qui n'a pas pu être établi malgré une tentative |

Ces marqueurs décrivent l'**état d'un texte**, jamais la valeur d'une personne.
`BLOQUÉ` et `ÉCHEC` signalent un obstacle documentaire, pas une insuffisance.

---

## 4. Compétence, preuve, objectif

Trois notions distinctes que l'usage courant confond souvent.

### Compétence

Ce que l'apprenant sait **comprendre, réaliser, raisonner ou expliquer** dans un
contexte professionnel. Une compétence peut être réelle et rester pourtant
indémontrable — c'est le cas le plus fréquent chez un autodidacte.

### Preuve

Ce qui rend la compétence **vérifiable** : exercice, configuration, résultat de
commande, démonstration, documentation, test, dépôt, compte rendu — toute
production observable et conservée.

### Objectif

Ce que l'apprenant cherche **encore à acquérir ou à démontrer**. Un objectif est
légitime et utile ; il ne doit pas être présenté comme acquis.

### Ne pas confondre

Ces quatre énoncés ne sont pas équivalents, et le livre les maintient séparés :

| Énoncé | Ce qu'il faut |
|---|---|
| « J'ai étudié ce sujet » | Une compréhension — mais l'étude seule n'est pas une compétence démontrée |
| « Je sais réaliser cette tâche » | Une pratique — qui doit encore être vérifiée |
| « Voici ma preuve » | Un artefact — qui doit encore être interprété |
| « Je sais expliquer mon travail » | Une capacité transversale — souvent la plus discriminante en entretien |

Un autodidacte en difficulté est souvent dans cet état : il a étudié, il sait faire, et
il n'a jamais produit la preuve ni la formulation. C'est précisément ce que ce
livre sert à corriger.

---

## 5. Comment lire les exercices

Les exercices sont des **instruments de progression professionnelle**, pas des
questions d'examen et non une préparation à un entretien.

Chaque exercice se lit selon la boucle des six temps :

```
comprendre → pratiquer → vérifier → produire une preuve
           → expliquer → identifier une limite
```

Pendant la réalisation, l'apprenant regarde simultanément cinq choses :

| Ce que l'on regarde | La question posée |
|---|---|
| **Ce que je comprends** | Est-ce que je connais la raison de ce choix, ou seulement sa forme ? |
| **Ce que je sais faire** | Est-ce que je peux le refaire sans chercher la commande ? |
| **Ce que je peux démontrer** | Ai-je un artefact produit par moi, pas un exemple recopié ? |
| **Ce que je peux expliquer** | Suis-je capable de défendre mes choix, y compris ceux que j'ai écartés ? |
| **Ce que je ne maîtrise pas** | Quel est le premier point à travailler après celui-ci ? |

### Exercices sans source

Certains chapitres sont des **canevas** : la situation opérationnelle est
présentée, les champs sont là, mais ils sont à renseigner par l'apprenant à
partir de son propre environnement.

```
ÉTAT : OBJECTIF / À CONSTRUIRE

Situation            : [à renseigner]
Problème opérationnel: [à renseigner]
Action               : [à renseigner]
Vérification         : [à effectuer]
Preuve produite      : [à produire]
Formulation          : [à construire]
Limite identifiée    : [à nommer]
```

Ces canevas ne sont jamais complétés par une expérience supposée. Une case vide
est une instruction ; elle ne doit pas être remplie par une plausible fiction.

---

## 6. L'entretien professionnel et ses équivalents

L'entretien est **un contexte d'expression des compétences**. Ce n'est pas la
finalité structurante de ce livre.

La même capacité — comprendre, justifier un choix, présenter un résultat,
expliquer un échec — se mobilise dans des contextes bien plus larges :

- la **documentation** d'une intervention ;
- une **revue par les pairs** ;
- une **passation** entre collègues ;
- une **intervention sur incident** ;
- une **discussion technique ou opérationnelle** avec un métier non technique ;
- une **situation professionnelle réelle**, y compris l'entretien.

Une compétence qui ne s'exprime qu'en entretien est une compétence fragile. Une
compétence qui s'exprime partout est une compétence professionnelle.

### Note sur la matrice des preuves

`annexes/MATRICE_PREUVES.md` est **intacte**. Sa colonne `Usage entretien` est
conservée telle quelle : elle constitue **l'état historique de la matrice à sa
date de création**.

L'interprétation professionnelle élargie portée par ce livre ne réécrit pas ce
livrable. Elle s'applique à sa lecture : les compétences qualifiées dans cette
colonne ont un usage plus large que l'entretien, dont l'entretien constitue un
cas particulier.

---

## 7. Structure du livre

| Partie | Intitulé | Cadre |
|---|---|---|
| **I** | **IDENTIFIER SON POSTE** | Métier, périmètre, responsabilités |
| **II** | Maîtriser le socle technique | Systèmes, réseaux, sécurité, exploitation |
| **III** | Opérer en environnement contraint | Sites isolés, énergie limitée, reprise |
| **IV** | Construire et présenter ses preuves | Laboratoire pratique, statut de chaque artefact |
| **V** | **EXPLIQUER ET DÉFENDRE SON TRAVAIL** | Entretien, documentation, revue par les pairs, passation |
| **VI** | **MISE EN SITUATION PROFESSIONNELLE** | Incident, astreinte, arbitrage, dialogue non technique |

### Sources et composantes

Le livre s'appuie sur trois corpus de `dossier_pret/`, qui sont des sources et
des composantes complémentaires :

| Corpus | Apport |
|---|---|
| `formation_it_officier/` | Socle pédagogique et technique : notions, exercices, progression |
| `git_workspace/` et `repos/` | Travaux pratiques et laboratoire de preuves : artefacts réels |
| `prep_entretien/` | Mise en situation professionnelle et expression des compétences |

`prep_entretien/` est **une composante du corpus, pas l'armature du livre**. Ses
modules servent la mise en situation et l'expression professionnelle ; ils ne
structurent pas l'ensemble et ne constituent pas sa finalité.

Le parcours reste cohérent pour un apprenant qui **ne se trouve pas en
préparation immédiate d'un entretien**. Dans ce cas, la partie V se lit comme une
formation à la documentation et à la revue par les pairs, et la partie VI comme une
formation à l'arbitrage et au dialogue non technique.

---

## 8. Lacunes et limites

Une lacune est une **information exploitable**, pas un défaut.

### La distinction à tenir

```
« Je n'ai pas encore démontré cette compétence »
        ≠
« Cette compétence n'existe pas »
```

La première est une constatation qui oriente le travail. La seconde est une
affirmation qui décourage à tort et qui n'a rien établi.

### Ce que le livre s'interdit

- Transformer une absence de preuve en affirmation d'absence de compétence.
- Transformer une difficulté en défaut personnel.
- Présenter un objectif comme une acquis.
- Combler une case vide d'un exercice par une expérience supposée.

### Ce qu'il fait

Chaque chapitre se termine, autant que possible, sur **ce qui n'est pas encore
maîtrisé**. Ce n'est pas une invitation rhétorique à la modestie : c'est l'inventaire
honnête de ce qui reste à travailler, et la base du chapitre suivant.

---

## 9. Conventions de lecture

| Élément | Convention |
|---|---|
| Commandes | Blocs `bash` — à saisir, pas à recopier sans lire |
| Chemins de fichiers | Chemin complet, vérifiable depuis `dossier_pret/` |
| Fichiers absents | Signalés explicitement — leur absence fait partie du constat |
| Informations manquantes | Marquées `N.D.` plutôt que reconstituées |
| Chiffres et mesures | Accompagnés de la commande et de la sortie qui les produisent |

Un chiffre sans la commande qui l'a produit n'est pas une donnée : c'est une
affirmation. Cette règle vaut pour tout l'ouvrage.

---

## 10. Par où commencer

| Si vous êtes… | Commencez par |
|---|---|
| Autodidacte avec de la pratique mais aucune preuve | Partie IV, puis la matrice des preuves |
| Autodidacte cherchant à structurer ses acquis | Partie I, puis II |
| Candidat à un entretien, avec un dossier déjà constitué | Partie V |
| Candidat sans pratique significative | Partie II, exercice par exercice |

Dans tous les cas, la **matrice des preuves** (`annexes/MATRICE_PREUVES.md`) est
le point de départ pratique : elle indique, compétence par compétence, ce qui
est démontré, déclaré, ou reste à produire.

Elle commence avec une colonne `DÉMONTRÉ` vide. **C'est l'état réel du dossier,
pas un défaut du livre.** C'est aussi le point à partir duquel la progression
devient mesurable.

Un fil rouge pédagogique transversal est conçu dans `annexes/FIL_ROUGE_CONCEPTION.md`.
Il sert à illustrer la méthode d'une partie à l'autre, sans pré-remplir les canevas
du lecteur et sans constituer une preuve de compétence.

Pour clore ce mode d'emploi, on rappellera la règle fondatrice : **un artefact
n'est pas automatiquement une preuve de compétence.** Les formules normatives
complètes du livre sont regroupées dans `annexes/PHRASE_MANIFESTE.md`.
