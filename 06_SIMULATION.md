# 06 — Simulation complète

**Partie VI — MISE EN SITUATION PROFESSIONNELLE**

Les situations de cette partie restent des **exercices**. Aucune simulation non
réalisée n'est présentée comme un résultat acquis, et les statuts établis dans
les parties précédentes ne sont pas modifiés par la lecture de ce chapitre.

---

## Introduction — Passer de la compétence isolée à la situation professionnelle

Les parties précédentes ont construit une progression :

```
se positionner → apprendre → pratiquer sous contrainte
              → produire des preuves → expliquer son travail
```

Il reste à réunir ces éléments dans une situation complète.

La simulation professionnelle ne sert pas à jouer artificiellement au
professionnel.

Elle sert à vérifier si l'apprenant peut mobiliser plusieurs compétences en même
temps : comprendre une demande ; définir un périmètre ; identifier les
contraintes ; observer avant d'agir ; formuler des hypothèses ; intervenir ;
vérifier ; produire une preuve ; expliquer ses choix ; documenter le résultat ;
reconnaître ses limites.

Une simulation réussie n'est donc pas nécessairement celle dans laquelle tout
fonctionne.

Elle peut également être réussie lorsque l'apprenant sait **qualifier correctement
ce qui fonctionne, ce qui échoue et ce qui reste non établi**.

---

## 1. Pourquoi simuler ?

Un exercice isolé permet de travailler une compétence.

Une simulation permet de vérifier la capacité à les relier.

Dans un environnement professionnel, le problème n'arrive pas toujours sous la
forme :

> « Exercice 4 — diagnostiquer un service HTTP. »

La demande peut être plus vague :

> « Le service n'est plus accessible. Pouvez-vous regarder ? »

L'IT doit alors déterminer : ce qui est attendu ; ce qui est observable ; ce qui a
changé ; ce qui est dans son périmètre ; ce qu'il peut tester ; ce qu'il ne doit
pas modifier sans autorisation.

La simulation reproduit cette complexité.

---

## 2. Une simulation n'est pas une preuve automatique

Le fait de réussir un exercice de simulation ne transforme pas automatiquement la
compétence en maîtrise générale.

La simulation doit elle-même être : réalisée ; observée ; vérifiée ; documentée.

```
SIMULATION → ACTION → OBSERVATION → VÉRIFICATION → PREUVE → STATUT
```

Si la simulation n'a pas été réalisée, elle reste un **OBJECTIF**.

Si elle a été réalisée mais sans résultat suffisamment vérifiable, le statut doit
rester adapté aux preuves disponibles.

---

## 3. Le contrat de simulation

Avant de commencer, définir le contrat.

| Élément | Définition |
|---|---|
| Situation | |
| Objectif | |
| Périmètre | |
| Ressources disponibles | |
| Contraintes | |
| Autorisations | |
| Temps prévu | |
| Critères de réussite | |
| Preuves attendues | |
| Limites connues | |

Le contrat évite qu'une simulation change de périmètre pendant son déroulement.

---

## 4. Le rôle de l'apprenant

Dans la simulation, l'apprenant doit agir comme responsable de son intervention.

Il ne doit pas attendre que chaque étape lui soit indiquée.

Il doit pouvoir dire :

> « Voici ce que je vais vérifier d'abord, et voici pourquoi. »

Cette autonomie ne signifie pas qu'il peut tout modifier.

Elle signifie qu'il sait **proposer une démarche dans le périmètre autorisé**.

---

## 5. Le rôle de l'environnement

L'environnement de simulation doit fournir suffisamment d'informations pour
travailler.

Il peut contenir volontairement : une configuration imparfaite ; un service
arrêté ; un port inattendu ; une dépendance manquante ; un problème de permissions
; une documentation incomplète ; une contrainte de ressources ; une information
absente.

Mais chaque élément doit être défini **avant** la simulation.

Il ne faut pas inventer après coup une cause pour expliquer le résultat.

---

## 6. Le principe : observer avant d'agir

Première règle de la simulation :

> **Ne pas corriger avant d'avoir établi l'état initial.**

Avant toute intervention, relever autant que possible : système ; ressources ;
services ; processus ; réseau ; stockage ; journaux utiles ; configuration
pertinente ; état attendu.

La première preuve de la simulation peut donc être l'état initial.

---

## 7. Étape 1 — Recevoir la demande

La demande initiale doit être traitée comme une demande professionnelle.

Questions à clarifier : quel est le problème observé ; depuis quand ; qui est
impacté ; quel comportement est attendu ; quel comportement est actuellement
observé ; y a-t-il eu un changement récent ; quelle est l'urgence ; quel est le
périmètre autorisé.

Ne pas commencer par une commande uniquement parce qu'elle est connue.

Commencer par comprendre le problème.

---

## 8. Étape 2 — Reformuler

> « Si je comprends bien, le service devrait être accessible depuis X, mais il ne
> répond actuellement pas depuis Y. Je vais d'abord vérifier l'état du service et
> son accessibilité avant toute modification. »

Cette reformulation permet de vérifier que le problème a été compris.

Elle constitue également un premier point de communication professionnelle.

---

## 9. Étape 3 — Définir le périmètre

Une simulation doit préciser ce qui est autorisé.

### Autorisé

consulter ; tester ; lire les journaux ; vérifier les processus ; vérifier les
ports ; modifier un fichier explicitement inclus dans le scénario.

### Non autorisé

supprimer des données ; réinitialiser le système ; installer arbitrairement des
logiciels ; modifier des secrets ; changer une configuration hors périmètre ;
redémarrer un service critique sans autorisation.

La compétence technique inclut la maîtrise du périmètre d'action.

---

## 10. Étape 4 — Établir l'état initial

Créer une fiche avant intervention.

| Élément | Observation |
|---|---|
| Heure / date | |
| Hôte | |
| Service concerné | |
| État du service | |
| Processus | |
| Port | |
| Réponse | |
| Ressources | |
| Journaux pertinents | |
| Configuration pertinente | |
| Anomalies observées | |

Cette fiche constitue la référence de comparaison.

---

## 11. Étape 5 — Formuler les hypothèses

Ne pas chercher immédiatement une cause unique.

Lister les hypothèses plausibles.

1. service arrêté ;
2. processus actif mais port incorrect ;
3. port bloqué ;
4. dépendance indisponible ;
5. configuration incorrecte ;
6. permissions insuffisantes ;
7. problème réseau ;
8. ressource insuffisante.

Puis choisir les tests permettant de distinguer ces hypothèses.

---

## 12. Étape 6 — Construire le plan de diagnostic

Le plan doit aller du plus simple au plus informatif.

```
processus → service → port → protocole → réponse → dépendance
```

| Test | Hypothèse ciblée | Résultat attendu | Résultat observé |
|---|---|---|---|
| | | | |
| | | | |
| | | | |

Cette méthode évite de lancer une succession de commandes sans raisonnement.

---

## 13. Étape 7 — Exécuter sans perdre les preuves

Pendant la simulation : conserver les résultats utiles ; noter les commandes
importantes ; noter les changements ; conserver les erreurs ; dater les
observations ; éviter les modifications inutiles.

Un terminal rempli de commandes ne constitue pas nécessairement une preuve
exploitable.

Il faut pouvoir reconstruire le raisonnement.

---

## 14. Étape 8 — Distinguer observation et interprétation

Pendant toute la simulation, utiliser deux colonnes :

| Observation | Interprétation |
|---|---|
| processus absent | le service pourrait être arrêté |
| port fermé | le service n'écoute peut-être pas |
| erreur dans le journal | cette erreur peut expliquer le symptôme |
| requête locale réussie | le service répond localement |

L'interprétation ne doit jamais être présentée comme un fait tant que le test ne
permet pas de l'établir.

---

## 15. Étape 9 — Agir uniquement après qualification

Une modification doit répondre à une hypothèse.

Avant l'action :

> « J'ai établi X. L'hypothèse Y reste compatible avec les observations. Je vais
> effectuer Z pour la tester ou la corriger. »

Après l'action :

> « Je vais maintenant vérifier si le comportement attendu est obtenu. »

La correction n'est pas la fin du diagnostic.

La vérification vient après.

---

## 16. Étape 10 — Vérifier le résultat

Après intervention, reprendre les critères initiaux.

```
avant → action → après
```

Questions : le service démarre-t-il ; le processus existe-t-il ; le port est-il
ouvert ; le protocole répond-il ; le résultat attendu est-il obtenu ; le
comportement est-il reproductible ; une régression est-elle apparue.

Ne jamais conclure « résolu » uniquement parce qu'une commande s'est terminée
sans erreur.

---

## 17. Étape 11 — Définir la limite de la conclusion

Une simulation peut démontrer :

> « le service répond localement dans l'environnement testé »

sans démontrer :

> « le service est prêt pour la production ».

La conclusion doit donc préciser son périmètre.

### Formule

> **Le test permet d'établir X dans le contexte Y. Il ne permet pas d'établir Z.**

Cette formulation doit devenir une habitude professionnelle.

---

## 18. Étape 12 — Produire le rapport

Le rapport final doit être court mais vérifiable.

```
1.  Demande
2.  État initial
3.  Observations
4.  Hypothèses
5.  Tests
6.  Actions
7.  Résultat
8.  Preuves conservées
9.  Limites
10. Recommandations ou suite autorisée
```

Chaque section est à renseigner par l'apprenant à partir de ce qu'il a réellement
constaté.

---

## 19. Simulation A — Service local indisponible

### Situation

Un service local est annoncé comme indisponible.

### Objectif

Déterminer où se situe le problème sans effectuer de modification non autorisée.

### Contraintes

accès local uniquement ; outils système disponibles ; aucune installation ; aucune
suppression ; modifications uniquement après autorisation.

### Questions

1. Le processus existe-t-il ?
2. Le service est-il actif ?
3. Quel port est attendu ?
4. Quel port est réellement utilisé ?
5. Le protocole répond-il ?
6. Que disent les journaux ?
7. Quelle hypothèse est confirmée ?
8. Quelle preuve peut être conservée ?

### Critère de réussite

Le candidat doit pouvoir expliquer son raisonnement et justifier sa conclusion à
partir des observations.

---

## 20. Simulation B — Diagnostic sous contrainte de ressources

### Situation

Une machine présente des lenteurs.

### Contraintes

mémoire limitée ; stockage limité ; peu d'outils disponibles ; aucune installation
pendant le diagnostic.

### Objectif

Identifier les ressources réellement disponibles avant de proposer une action.

### Travail demandé

Mesurer : mémoire ; charge ; processus ; stockage ; espace disponible ; éventuelle
activité excessive.

Puis distinguer :

```
symptôme → mesure → hypothèse → vérification
```

### Critère

Aucune cause ne doit être affirmée uniquement sur la base du symptôme initial.

---

## 21. Simulation C — Sauvegarde et restauration

### Situation

Une sauvegarde existe mais personne ne sait si elle peut être restaurée.

### Objectif

Établir ce que la sauvegarde permet réellement de restaurer.

### Travail

1. Identifier la sauvegarde.
2. Vérifier son état.
3. Définir un environnement de restauration.
4. Restaurer les éléments autorisés.
5. Vérifier leur intégrité.
6. Documenter le résultat.
7. Identifier les éléments non testés.

### Point pédagogique

> **Une sauvegarde qui n'a jamais été restaurée reste une hypothèse de récupération.**

La simulation doit apprendre à distinguer :

```
existence de la sauvegarde → intégrité → restauration → vérification fonctionnelle
```

---

## 22. Simulation D — Réseau isolé

### Situation

Deux machines doivent communiquer dans un réseau local sans accès Internet.

### Objectif

Diagnostiquer la connectivité et un service applicatif.

```
interface → adresse IP → route → voisinage → port → protocole → application
```

Ne pas commencer par modifier l'adresse IP.

Commencer par observer.

### Critère

Le candidat doit pouvoir identifier le niveau exact auquel la communication échoue.

---

## 23. Simulation E — Projet applicatif incomplet

### Situation

Un projet contient une architecture et du code, mais son fonctionnement complet
n'est pas démontré.

### Objectif

Qualifier précisément son état sans le surévaluer.

### Questions

- Quels composants existent ?
- Quels composants sont configurés ?
- Quels composants ont été exécutés ?
- Quels tests existent ?
- Quels artefacts de résultat existent ?
- Quelles dépendances restent à vérifier ?
- Qu'est-ce qui est seulement déclaré ?

Cette simulation est particulièrement importante pour l'autodidacte.

Elle apprend à dire :

> « Le projet existe »

sans en déduire automatiquement :

> « Le projet est fonctionnel et reproductible. »

---

## 24. Simulation F — Reprise d'un travail par un tiers

### Situation

Un autre IT doit reprendre un projet que vous avez commencé.

Il n'a pas votre mémoire du projet.

### Il doit pouvoir trouver

objectif ; architecture ; prérequis ; installation ; configuration ; procédures ;
tests ; résultats ; erreurs connues ; limites ; sauvegardes ; points de
surveillance.

### Critère

Le tiers doit pouvoir comprendre le projet sans explication orale permanente.

Si cela échoue, la documentation doit être améliorée.

---

## 25. Simulation G — Demande ambiguë

### Situation

Un responsable demande :

> « Pouvez-vous sécuriser cette machine ? »

La demande est trop vague pour agir directement.

### Travail attendu

Transformer la demande en questions : quelle machine ; quel périmètre ; quelle
menace ; quel niveau de sécurité attendu ; quelles contraintes ; quelles
modifications sont autorisées ; quelles exigences de disponibilité ; quelles
mesures existent déjà ; comment vérifier le résultat.

La compétence évaluée n'est pas la quantité de commandes exécutées.

C'est la capacité à **clarifier avant d'agir**.

---

## 26. Simulation H — Incident avec information manquante

### Situation

Une information importante n'est pas disponible.

Exemples : historique absent ; journal incomplet ; configuration inconnue ; accès
manquant ; version inconnue.

### Travail attendu

Ne pas inventer l'information.

Marquer **NON ÉTABLI**, puis identifier : pourquoi l'information manque ; quelle
observation serait nécessaire ; si cette observation est possible ; quelle
conclusion reste néanmoins autorisée.

Une information manquante est une donnée du diagnostic.

---

## 27. Simulation I — Revue technique

### Situation

Un collègue présente une solution.

L'objectif n'est pas de savoir qui a raison immédiatement.

Il faut examiner : objectif ; hypothèses ; architecture ; sécurité ; dépendances ;
tests ; preuves ; reproductibilité ; limites.

### Questions utiles

> « Quel problème ce choix résout-il ? »

> « Comment avez-vous vérifié ce comportement ? »

> « Quelle hypothèse soutient ce choix ? »

> « Qu'est-ce qui n'a pas encore été testé ? »

La revue devient une pratique d'apprentissage mutuel.

---

## 28. Simulation J — Présentation complète d'un projet

Cette simulation réunit les compétences travaillées depuis le début du livre.

### Présentation en dix minutes

| Minute | Contenu |
|---|---|
| 1 | **Contexte** — Quel problème ? |
| 2 | **Contraintes** — Dans quel environnement ? |
| 3 | **Architecture** — Quels composants ? |
| 4 | **Rôle personnel** — Qu'avez-vous réellement fait ? |
| 5 | **Difficulté** — Quel problème avez-vous rencontré ? |
| 6 | **Diagnostic** — Comment l'avez-vous analysé ? |
| 7 | **Preuve** — Comment avez-vous vérifié ? |
| 8 | **Résultat** — Qu'est-ce qui est établi ? |
| 9 | **Limites** — Qu'est-ce qui reste à démontrer ? |
| 10 | **Progression** — Que devez-vous encore apprendre ou améliorer ? |

---

## 29. La grille d'observation

Une simulation doit être évaluée à partir de comportements observables.

| Critère | Observation |
|---|---|
| Compréhension de la demande | |
| Définition du périmètre | |
| Observation initiale | |
| Raisonnement par hypothèses | |
| Choix des tests | |
| Respect des autorisations | |
| Qualité des actions | |
| Vérification | |
| Conservation des preuves | |
| Communication | |
| Documentation | |
| Identification des limites | |

Éviter les évaluations vagues telles que :

> « Bon professionnel »

ou :

> « Niveau insuffisant »

sans observation associée.

---

## 30. Les trois niveaux de résultat

Après une simulation, distinguer trois choses.

### Niveau 1 — La tâche

L'action a-t-elle été réalisée ?

### Niveau 2 — Le résultat

Le comportement attendu a-t-il été obtenu ?

### Niveau 3 — La compétence

L'apprenant peut-il expliquer, reproduire et adapter la démarche ?

Une seule réussite ne suffit pas nécessairement à établir le troisième niveau.

---

## 31. Auto-évaluation après simulation

Immédiatement après l'exercice, répondre :

### Ce que j'ai réussi

> …

### Ce que j'ai observé

> …

### Ce que j'ai vérifié

> …

### Ce qui a échoué

> …

### Ce que je n'ai pas pu établir

> …

### Ce que je ferais différemment

> …

### Ce que je dois encore apprendre

> …

Cette fiche transforme la simulation en boucle d'apprentissage.

---

## 32. Le journal de simulation

Conserver un journal minimal :

| Date | Simulation | Objectif | Résultat | Preuve | Limite |
|---|---|---|---|---|---|
| | | | | | |
| | | | | | |
| | | | | | |

Le journal permet de suivre la progression sans réécrire toute l'expérience.

---

## 33. Corriger après une simulation

Une correction doit être liée à une observation.

### À éviter

> « Je dois devenir meilleur en réseau. »

### À privilégier

> « Lors du diagnostic, je n'ai pas vérifié la route avant de tester le service. Je
> dois intégrer cette vérification dans ma chaîne de diagnostic. »

La seconde formulation produit un objectif d'apprentissage concret.

---

## 34. Le plan de correction personnel

Après plusieurs simulations, regrouper les difficultés.

| Difficulté observée | Cause probable | Action d'apprentissage | Preuve attendue |
|---|---|---|---|
| | | | |
| | | | |
| | | | |

Une difficulté non transformée en action d'apprentissage risque de se répéter.

Une action d'apprentissage sans preuve risque de rester une intention.

---

## 35. Simulation finale intégrée

La simulation finale doit réunir au minimum : une demande ambiguë ; une
contrainte matérielle ou réseau ; un problème technique ; une information
manquante ; un diagnostic ; une intervention autorisée ; une vérification ; une
preuve ; une présentation orale ; une documentation courte.

Le scénario peut être adapté au matériel réellement disponible.

Il n'est pas nécessaire de disposer d'une infrastructure professionnelle.

Un environnement local suffisamment contrôlé peut servir de laboratoire.

---

## 36. Contrat de la simulation finale

Avant de commencer :

```
Situation           : ______________________
Demande reçue       : ______________________
Périmètre           : ______________________
Contraintes         : ______________________
Ressources          : ______________________
Autorisations       : ______________________
Critères de réussite: ______________________
Preuves attendues   : ______________________
Durée              : ______________________
```

Le scénario ne doit pas être modifié pour masquer une difficulté rencontrée.

---

## 37. Déroulement de la simulation finale

| Phase | Contenu |
|---|---|
| **A — Comprendre** | Recevoir la demande et reformuler |
| **B — Observer** | Établir l'état initial |
| **C — Diagnostiquer** | Formuler et tester les hypothèses |
| **D — Agir** | Effectuer uniquement les actions autorisées |
| **E — Vérifier** | Comparer l'état obtenu au résultat attendu |
| **F — Documenter** | Conserver les observations et preuves |
| **G — Expliquer** | Présenter la démarche en quelques minutes |
| **H — Analyser** | Identifier les limites et les apprentissages |

---

## 38. Critères de réussite de la simulation finale

La simulation est considérée comme réussie lorsque l'apprenant peut :

1. reformuler correctement la demande ;
2. définir son périmètre ;
3. observer avant de modifier ;
4. formuler des hypothèses ;
5. choisir des tests pertinents ;
6. respecter les autorisations ;
7. vérifier le résultat après action ;
8. conserver une preuve exploitable ;
9. expliquer ce qui est établi et ce qui ne l'est pas ;
10. produire une documentation permettant la reprise.

La réussite ne signifie pas que toutes les hypothèses initiales étaient correctes.

Une hypothèse éliminée par un test constitue également une information utile.

---

## 39. Ce que la simulation doit produire

À la fin du parcours, l'apprenant devrait pouvoir produire un petit dossier
professionnel comprenant : une fiche de contexte ; un état initial ; un plan de
diagnostic ; les observations importantes ; les actions réalisées ; les résultats ;
les preuves ; les limites ; une synthèse ; une présentation orale courte ; un plan
de progression.

Ce dossier devient une trace du travail accompli.

Il ne doit contenir que des résultats réellement obtenus.

---

## 40. Résultat attendu — devenir capable d'agir sous contrainte

Le parcours complet aboutit à une compétence plus large que la connaissance d'une
liste d'outils.

L'IT autodidacte doit progressivement devenir capable de : comprendre une
situation ; définir son périmètre ; observer avant d'agir ; raisonner à partir
d'hypothèses ; intervenir avec contrôle ; vérifier le résultat ; produire une
preuve ; expliquer son travail ; documenter ce qui a été fait ; reconnaître ce
qui reste à apprendre.

La compétence professionnelle peut alors être représentée par la boucle
complète :

```
POSITIONNEMENT → COMPRÉHENSION → PRATIQUE → CONTRAINTE
              → DIAGNOSTIC → ACTION → VÉRIFICATION → PREUVE
              → EXPLICATION → TRANSMISSION → PROGRESSION
```

Cette boucle ne s'arrête pas avec la fin du livre.

Elle constitue une méthode de professionnalisation continue.

---

## Synthèse — La simulation comme épreuve de cohérence

Une simulation complète ne cherche pas à reproduire artificiellement une journée
de travail.

Elle vérifie une cohérence :

```
ce que je prétends savoir → ce que je sais réellement faire
                        → ce que je peux vérifier
                        → ce que je peux démontrer
                        → ce que je peux expliquer
```

Elle permet également d'identifier les écarts.

Un résultat non obtenu n'est pas automatiquement un échec global.

Une contrainte bloquante n'est pas automatiquement une faute.

Une information manquante n'est pas une invitation à inventer.

Une hypothèse abandonnée n'est pas du temps perdu.

Ces situations deviennent utiles lorsqu'elles sont qualifiées et documentées.

Le parcours de l'IT autodidacte ne consiste donc pas à accumuler des technologies.

Il consiste à construire progressivement une capacité professionnelle vérifiable :

> **comprendre → pratiquer → vérifier → prouver → expliquer → transmettre →
> progresser.**