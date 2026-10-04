# 02 — Socle technique

**Partie II — MAÎTRISER LE SOCLE TECHNIQUE**

Cette partie constitue le cœur de formation technique du livre. Elle suit les
notions selon la boucle : comprendre, pratiquer, vérifier, produire une preuve,
expliquer, identifier une limite.

Les domaines non suffisamment documentés dans les sources restent des
**objectifs d'apprentissage**. Les dépôts du laboratoire servent d'exemples de
preuves **et** de limites, sans jamais transformer leur contenu en validation
opérationnelle.

Le fil rouge pédagogique se poursuit ici par un périmètre technique volontairement réduit.
Il sert à montrer comment structurer une pratique, sans remplacer le socle technique
réellement exercé par le lecteur.

---

## 1. Pourquoi un socle technique ?

Un IT autodidacte peut avoir appris beaucoup de technologies sans avoir construit
une représentation suffisamment structurée des systèmes qu'il administre.

Le but de cette partie n'est donc pas d'accumuler des commandes.

Il s'agit de construire une méthode permettant de passer de :

```
notion → manipulation → vérification → diagnostic
       → documentation → preuve
```

Un professionnel doit pouvoir expliquer non seulement **comment** effectuer une
opération, mais également :

- pourquoi elle est nécessaire ;
- quelles dépendances elle possède ;
- comment vérifier son résultat ;
- quels risques elle introduit ;
- comment revenir en arrière ;
- comment diagnostiquer son échec ;
- comment transmettre la procédure à quelqu'un d'autre.

---

## 2. Le socle avant les technologies

Avant de mémoriser des outils, il faut comprendre les couches fondamentales d'un
système informatique.

### Couche 1 — Matériel et ressources

Identifier :

- processeur ;
- mémoire ;
- stockage ;
- interfaces réseau ;
- périphériques ;
- alimentation ;
- contraintes physiques.

Questions à savoir poser :

- Quelle ressource est limitée ?
- Quelle ressource est saturée ?
- Quelle ressource est indisponible ?
- Comment distinguer une panne matérielle d'une panne logicielle ?

### Couche 2 — Système

Comprendre :

- processus ;
- utilisateurs ;
- groupes ;
- permissions ;
- fichiers ;
- services ;
- journaux ;
- processus de démarrage ;
- espace disque ;
- mémoire ;
- réseau.

### Couche 3 — Services

Un système devient utile lorsqu'il fournit des services :

- HTTP ;
- DNS ;
- SSH ;
- base de données ;
- sauvegarde ;
- supervision ;
- authentification ;
- partage de fichiers.

### Couche 4 — Utilisateur et métier

Le service technique existe pour répondre à un besoin.

Il faut donc toujours pouvoir relier :

```
infrastructure → service → utilisateur → besoin métier
```

Cette dernière relation est essentielle dans un poste d'IT Officer.

---

## 3. Linux : apprendre à administrer avant d'automatiser

Linux constitue un socle particulièrement important pour l'administration système.

L'objectif n'est pas de connaître une liste de commandes par cœur.

Il faut savoir observer un système.

### 3.1 Navigation et identification

Un premier niveau consiste à savoir :

- identifier le système ;
- connaître son emplacement courant ;
- parcourir l'arborescence ;
- identifier les fichiers ;
- lire leur contenu ;
- rechercher une information.

#### Exercice

Sur une machine de laboratoire :

1. identifier le système ;
2. identifier l'utilisateur courant ;
3. identifier le répertoire courant ;
4. examiner l'arborescence ;
5. localiser un fichier précis ;
6. consulter son contenu ;
7. documenter les commandes utilisées.

**Preuve attendue** : un journal de travail contenant *commande*, *résultat*,
*interprétation*.

### 3.2 Utilisateurs, groupes et permissions

Il faut comprendre la différence entre :

- propriétaire ;
- groupe ;
- autres utilisateurs ;
- lecture ;
- écriture ;
- exécution.

Mais la compétence ne se limite pas à modifier une permission.

Il faut pouvoir répondre :

> Qui doit accéder à cette ressource, pourquoi et avec quel niveau d'accès ?

#### Exercice

Créer une ressource partagée entre deux groupes d'utilisateurs fictifs.

Vérifier : accès autorisé, accès refusé, propriétaire, groupe, permissions,
comportement après modification.

**Preuve attendue** :

| Élément | État attendu | Résultat observé |
|---|---|---|
| Utilisateur A | accès | |
| Utilisateur B | accès | |
| Utilisateur C | refus | |
| Propriétaire | correct | |
| Groupe | correct | |

---

## 4. Services et processus

Un service informatique n'est pas seulement un programme installé.

Il faut comprendre son cycle de vie :

```
installation → configuration → démarrage → fonctionnement
            → supervision → arrêt → récupération
```

Pour un service donné, savoir répondre :

- Quel processus l'exécute ?
- Sur quelle adresse écoute-t-il ?
- Sur quel port ?
- Avec quel utilisateur ?
- Où sont ses journaux ?
- Quelle configuration utilise-t-il ?
- Que se passe-t-il s'il s'arrête ?
- Comment vérifier son état ?

#### Exercice

Mettre en place un petit service HTTP de laboratoire. Puis vérifier séparément :
que le processus existe ; que le port est ouvert localement ; que le service
répond ; que les journaux sont disponibles ; que l'arrêt du service produit un
état identifiable.

### Règle

> **Un service qui démarre n'est pas nécessairement un service fonctionnel.**

Il faut vérifier son comportement réel.

---

## 5. Réseau : raisonner par couches

Un autodidacte peut connaître VLAN, DNS, VPN ou pare-feu sans toujours disposer
d'une méthode de diagnostic suffisamment structurée.

Le diagnostic réseau doit commencer par le plus bas niveau pertinent.

### Chaîne de diagnostic

```
interface → adresse → route → résolution
         → connectivité → port → protocole → application
```

Lorsqu'un service distant ne répond pas :

1. l'interface fonctionne-t-elle ?
2. l'adresse est-elle correcte ?
3. la route existe-t-elle ?
4. le nom se résout-il ?
5. la destination est-elle joignable ?
6. le port est-il accessible ?
7. le protocole répond-il ?
8. l'application fonctionne-t-elle ?

Cette méthode évite de modifier simultanément plusieurs éléments.

### 5.1 DNS

Comprendre : résolution de noms, serveur DNS, enregistrement, cache, résolution
directe, résolution inverse, différence entre problème DNS et problème réseau.

#### Exercice

Construire un petit scénario de résolution locale. Vérifier : nom demandé,
serveur interrogé, adresse retournée, résultat attendu, résultat observé.

### 5.2 VLAN

Un VLAN doit être compris comme une séparation logique du réseau.

Le lecteur doit savoir expliquer : pourquoi segmenter ; qui peut communiquer avec
qui ; où intervient le routage ; où intervient le pare-feu ; comment vérifier la
configuration.

L'objectif n'est pas de mémoriser une syntaxe particulière.

### 5.3 VPN

Un VPN doit être étudié selon quatre questions :

1. Qui établit le tunnel ?
2. Quelles adresses sont utilisées ?
3. Quels réseaux doivent être accessibles ?
4. Comment vérifier que le trafic passe réellement par le tunnel ?

Un fichier de configuration VPN constitue une **configuration**, pas
automatiquement une preuve de fonctionnement.

---

## 6. Sécurité : protéger avant de complexifier

La sécurité informatique commence par la maîtrise de la surface exposée.

Le raisonnement de base est :

```
identifier → réduire → contrôler → journaliser → vérifier
```

### 6.1 Comptes et privilèges

Questions fondamentales :

- Qui possède un compte ?
- Quels privilèges possède-t-il ?
- Pourquoi ?
- Combien de temps ces privilèges sont-ils nécessaires ?
- Comment les retirer ?

### 6.2 Secrets

Les secrets ne doivent pas être mélangés au code source lorsque cela peut être
évité.

Identifier : mots de passe, clés, jetons, certificats, variables sensibles. Puis
séparer :

```
code → configuration → secret
```

Un `.env.example` documente une structure de configuration ; il ne constitue pas
une preuve qu'un système complet est sécurisé.

### 6.3 Audit

Un audit doit produire des observations vérifiables.

Il faut distinguer : état observé ; risque identifié ; recommandation ;
correction ; vérification après correction.

Ne pas confondre :

> « Cette configuration est recommandée »

avec :

> « Cette configuration est effectivement appliquée et vérifiée. »

---

## 7. Sauvegarde et restauration

Une sauvegarde n'est utile que si les données peuvent être récupérées.

Le raisonnement complet est :

```
données → sauvegarde → conservation → vérification → restauration
```

### 7.1 Questions fondamentales

Pour une politique de sauvegarde :

- Quelles données sont critiques ?
- À quelle fréquence les sauvegarder ?
- Où les stocker ?
- Combien de copies conserver ?
- Comment les protéger ?
- Combien de temps les conserver ?
- Comment vérifier leur intégrité ?
- Comment restaurer ?

### 7.2 Le test de restauration

Une tâche planifiée qui produit un fichier de sauvegarde ne démontre pas à elle
seule que la récupération fonctionne.

#### Exercice

Créer une petite donnée de test. Puis : la sauvegarder ; vérifier la présence de
la sauvegarde ; simuler sa disparition ; restaurer ; vérifier le contenu
restauré ; documenter le résultat.

**Preuve attendue** :

| Étape | Attendu | Observé |
|---|---|---|
| Création | donnée présente | |
| Sauvegarde | copie créée | |
| Suppression simulée | original absent | |
| Restauration | original récupéré | |
| Vérification | contenu identique | |

---

## 8. Scripting : automatiser sans perdre le contrôle

L'automatisation est une compétence d'administration, pas une fin en soi.

Un bon script doit être : lisible ; prévisible ; contrôlable ; documenté ;
suffisamment robuste ; adapté à son environnement.

Pour chaque script, se demander :

- Que fait-il ?
- Quelles entrées accepte-t-il ?
- Quelles dépendances possède-t-il ?
- Que se passe-t-il en cas d'erreur ?
- Peut-il être relancé ?
- Quelles données modifie-t-il ?
- Comment vérifier son résultat ?

#### Exercice

Choisir une tâche administrative répétitive. Produire : une procédure manuelle ;
un script ; une vérification du résultat ; une documentation d'utilisation.

### Règle

> **Automatiser une procédure mal comprise ne la rend pas plus fiable.**

---

## 9. Conteneurs : comprendre avant de déployer

Docker et Compose doivent être étudiés comme des mécanismes d'isolation et
d'orchestration de services.

Le lecteur doit comprendre : image ; conteneur ; volume ; réseau ; port ;
variable d'environnement ; dépendance ; cycle de vie.

### Exercice progressif

| Niveau | Opération |
|---|---|
| 1 | Lancer un service simple |
| 2 | Ajouter une configuration |
| 3 | Ajouter une persistance |
| 4 | Ajouter un second service |
| 5 | Vérifier les communications |
| 6 | Arrêter puis redémarrer l'ensemble |

À chaque niveau : **configurer → démarrer → observer → vérifier → documenter**.

Un fichier `docker-compose.yml` prouve l'existence d'une configuration
déclarative. Il ne prouve pas à lui seul que les services ont été exécutés avec
succès.

Cette distinction est particulièrement importante pour l'analyse des projets de
ce livre. Les audits du laboratoire ont identifié des configurations et des
scripts, mais **les preuves d'exécution n'ont pas été établies par les audits
eux-mêmes**.

---

## 10. Virtualisation

La virtualisation doit être comprise à travers les ressources qu'elle abstrait :
CPU, mémoire, stockage, réseau, périphériques.

Pour une machine virtuelle, savoir expliquer : ce qu'elle virtualise ; quelles
ressources lui sont attribuées ; comment elle communique avec l'hôte ; comment
elle stocke ses données ; comment elle est sauvegardée ; comment elle est
restaurée.

Le référentiel contient des objectifs autour de la virtualisation, mais une
fiche ou une configuration ne doit pas être présentée comme une preuve
d'administration effective.

---

## 11. Supervision : observer avant d'intervenir

La supervision répond à une question fondamentale :

> **Comment savoir qu'un système fonctionne lorsque personne ne le regarde ?**

Elle doit couvrir au minimum : disponibilité, CPU, mémoire, stockage, réseau,
services, journaux, seuils, alertes.

Une bonne supervision doit permettre de distinguer :

```
symptôme → événement → cause possible → action
```

#### Exercice

Choisir un service et définir :

| Élément | Définition |
|---|---|
| Indicateur | |
| Seuil | |
| Alerte | |
| Cause possible | |
| Action | |
| Vérification après action | |

---

## 12. Documentation opérationnelle

La documentation fait partie de la compétence technique.

Une procédure utile doit permettre à une autre personne de comprendre : le
contexte ; les prérequis ; les étapes ; les commandes ; le résultat attendu ;
les erreurs possibles ; la récupération ; les limites.

### Mauvaise documentation

> Installer le service puis vérifier qu'il fonctionne.

### Documentation exploitable

Elle précise : où effectuer l'opération ; avec quel compte ; quelles dépendances
sont nécessaires ; quelle commande utiliser ; quel résultat attendre ; comment
interpréter un résultat différent ; comment revenir à l'état précédent.

---

## 13. Les travaux pratiques du référentiel

Le référentiel de formation constitue une progression, pas une certification
automatique.

Les exercices disponibles permettent notamment de travailler : navigation système ;
permissions ; partage de ressources ; service HTTP ; sauvegarde ; audit système.

Certains exercices restent incomplets dans les sources. Ils doivent donc être
traités comme des **travaux à compléter**, et non comme des compétences déjà
validées.

Le lecteur doit conserver cette distinction :

> **Un exercice décrit une occasion de pratiquer. Il ne constitue une preuve
> qu'après réalisation et vérification.**

---

## 14. Helm et l'orchestration

L'existence d'un chart Helm permet d'introduire une autre forme de configuration
déclarative.

Mais le lecteur doit distinguer : structure du chart ; templates ; valeurs ;
rendu attendu ; déploiement réel ; vérification du service déployé.

Le même principe s'applique ici :

```
configuration ≠ exécution ≠ preuve de fonctionnement
```

L'objectif pédagogique est d'apprendre à passer progressivement de la
configuration déclarative à la vérification opérationnelle.

---

## 15. Relier les domaines techniques

Les compétences ne doivent pas rester isolées.

Un scénario professionnel peut mobiliser simultanément :

```
Linux → réseau → sécurité → service → sauvegarde
      → supervision → automatisation → documentation
```

Déployer un service interne peut nécessiter : un système Linux ; un compte de
service ; une configuration réseau ; une règle de pare-feu ; un service
applicatif ; une sauvegarde ; une supervision ; une procédure de restauration ;
un script d'administration ; une documentation.

C'est cette intégration qui rapproche progressivement l'exercice pédagogique
d'une situation professionnelle.

---

## 16. La méthode de diagnostic

Lorsqu'un problème apparaît, éviter la modification immédiate.

Utiliser une boucle contrôlée :

| Étape | Question |
|---|---|
| **Observer** | Que se passe-t-il réellement ? |
| **Décrire** | Quel est le symptôme exact ? |
| **Isoler** | Quelle couche peut être responsable ? |
| **Formuler une hypothèse** | Quelle explication est compatible avec les observations ? |
| **Vérifier** | Quelle observation confirmerait ou écarterait cette hypothèse ? |
| **Agir** | Modifier uniquement ce qui est nécessaire |
| **Vérifier à nouveau** | Le problème est-il réellement résolu ? |
| **Documenter** | Qu'est-ce qui a été observé, modifié et vérifié ? |

Cette méthode protège contre le diagnostic par intuition.

---

## 17. Le laboratoire de preuves

Les dépôts du dossier constituent un laboratoire particulièrement utile pour
apprendre cette distinction.

Les audits ont montré trois situations différentes.

**`scripts-admin`** — des scripts Bash sont effectivement présents et structurés,
mais leur simple présence ne démontre pas leur exécution en conditions réelles.

**`infra-as-code`** — des fichiers Compose, des scripts et des structures Ansible
existent, mais l'état observé ne permet pas de conclure à une exécution complète
de l'infrastructure.

**`pi-kiosk-offline`** — la documentation décrit une architecture, alors que le
dépôt inspecté ne fournit pas l'ensemble des exécutables correspondants.

Ces exemples enseignent une règle essentielle :

> **Ce que l'on sait expliquer n'est pas nécessairement ce que l'on sait
> exécuter.**

Et inversement :

> **Ce que l'on a exécuté une fois n'est pas nécessairement ce que l'on sait
> administrer de manière reproductible.**

---

## 18. Les trois niveaux de pratique

Pour chaque compétence, rechercher progressivement trois niveaux.

### Niveau 1 — Comprendre

Je peux expliquer le principe.

### Niveau 2 — Pratiquer

Je peux réaliser l'opération dans un environnement contrôlé.

### Niveau 3 — Exploiter

Je peux : diagnostiquer ; sécuriser ; automatiser ; documenter ; restaurer ;
transmettre.

Le passage d'un niveau à l'autre doit être matérialisé par des exercices et des
preuves.

---

## 19. Le cahier de laboratoire

Pour chaque exercice technique, conserver une fiche simple.

```text
COMPÉTENCE :
DATE :
ENVIRONNEMENT :

OBJECTIF :
PRÉREQUIS :

OPÉRATIONS RÉALISÉES :

OBSERVATIONS :

ERREURS RENCONTRÉES :

DIAGNOSTIC :

CORRECTION :

VÉRIFICATION :

PREUVE PRODUITE :

LIMITES :

CE QUE JE SAIS MAINTENANT EXPLIQUER :
```

Cette fiche transforme une manipulation ponctuelle en expérience exploitable.

---

## 20. Quand considérer un exercice comme terminé ?

Un exercice n'est pas terminé parce que la commande ne retourne plus d'erreur.

Il est terminé lorsque le lecteur peut répondre aux questions suivantes :

- Qu'est-ce que j'ai voulu obtenir ?
- Qu'ai-je réellement fait ?
- Quel résultat ai-je obtenu ?
- Comment l'ai-je vérifié ?
- Que se passerait-il en cas d'échec ?
- Comment revenir en arrière ?
- Quelle preuve ai-je conservée ?
- Quelles limites restent présentes ?

Si une réponse manque, l'exercice peut rester ouvert.

---

## 21. La matrice de progression

Utiliser `annexes/MATRICE_PREUVES.md` comme tableau de pilotage.

Pour chaque compétence :

```
Source → Observable → Preuve d'exécution → Statut → Formulation professionnelle
```

Ne pas remplir artificiellement une case pour donner l'impression d'une
progression.

Une compétence sans preuve peut rester **déclarée**, **objective** ou **non
établie** selon les éléments disponibles.

La matrice n'est donc pas seulement un outil d'évaluation. Elle apprend au
lecteur une discipline professionnelle :

> **ne jamais présenter comme démontré ce qui ne l'est pas.**

---

## 22. Domaines à approfondir

Certains domaines peuvent apparaître dans un référentiel professionnel sans
disposer d'un parcours pratique suffisamment documenté dans les sources.

Ils doivent rester identifiés comme objectifs de formation. Cela peut notamment
concerner : Windows Server ; Active Directory ; virtualisation avancée ;
SAN/NAS/RAID ; normes et référentiels de sécurité ; ITIL ; méthodes de travail ;
leadership ; gestion budgétaire.

La bonne formulation n'est pas :

> « Je maîtrise ces domaines »

mais :

> « Ces domaines font partie de mon plan de professionnalisation et je dois encore
> produire les pratiques et preuves correspondantes. »

---

## 23. Le socle technique comme système

À la fin de cette partie, le lecteur doit commencer à voir l'IT non comme une
collection de technologies mais comme un système de dépendances.

Un service dépend : d'un système ; de ressources ; d'un réseau ; d'une
configuration ; d'une sécurité ; parfois d'une donnée persistante ; d'une
supervision ; d'une procédure de récupération.

Une compétence professionnelle consiste à comprendre ces dépendances et à agir
sur elles avec méthode.

---

## 24. Exercice final — construire un mini-service professionnel

Choisir un service simple de laboratoire. Produire successivement :

### Étape 1 — Architecture

Décrire : système ; réseau ; service ; données ; utilisateurs.

### Étape 2 — Installation

Installer ou configurer le service dans un environnement contrôlé.

### Étape 3 — Vérification

Démontrer : disponibilité ; accès ; comportement attendu.

### Étape 4 — Sécurité

Identifier : comptes ; permissions ; exposition réseau ; secrets.

### Étape 5 — Sauvegarde

Définir : données à sauvegarder ; emplacement ; fréquence ; restauration.

### Étape 6 — Supervision

Définir : indicateur ; seuil ; alerte ; action.

### Étape 7 — Automatisation

Automatiser au moins une opération répétitive.

### Étape 8 — Documentation

Rédiger une procédure permettant à une autre personne de reproduire l'opération.

### Étape 9 — Preuve

Conserver les éléments permettant de démontrer ce qui a réellement été exécuté.

### Étape 10 — Retour d'expérience

Documenter : ce qui a fonctionné ; ce qui a échoué ; ce qui a été corrigé ; ce
qui reste à améliorer.

---

## 25. Résultat attendu

La maîtrise du socle technique ne signifie pas connaître toutes les
technologies.

Elle signifie savoir :

```
observer → comprendre → agir → vérifier → sécuriser
        → automatiser → documenter → récupérer
```

L'IT autodidacte progresse lorsque chaque nouvelle technologie devient une
nouvelle occasion d'appliquer cette méthode.

La Partie suivante élargira cette logique aux environnements où les
contraintes de réseau, d'énergie, de matériel, de disponibilité ou d'accès
rendent cette discipline particulièrement importante.
