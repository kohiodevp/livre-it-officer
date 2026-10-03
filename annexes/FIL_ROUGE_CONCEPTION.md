# FIL ROUGE — CONCEPTION

> Ce fichier est un document de conception.
>
> Il ne modifie pas le corps du livre.
> Il ne pré-remplit pas les canevas du lecteur.
> Il ne constitue pas une preuve de compétence.
>
> Son objet est de préparer l'introduction d'un cas fil rouge transversal,
> en définissant son périmètre, ses contraintes, ses livrables par partie
> et ses critères de non-régression.

---

## 1. Principe du fil rouge

Un fil rouge est un cas pédagogique transversal. Il sert à montrer comment la méthode
s'applique de partie en partie, sur un même contexte. Il ne remplace pas le travail du
lecteur et ne devient jamais une preuve de compétence.

Trois distinctions doivent rester visibles en permanence :

```
cas fil rouge ≠ dossier du lecteur
document de conception ≠ exemple rempli dans un canevas
démonstration pédagogique ≠ compétence démontrée
```

Le corpus a déjà tranché cette question. Les canevas des parties 01, 03, 04, 05 et 06
sont volontairement vides, et le fichier qui porte les exemples — `EXEMPLES_PEDAGOGIQUES.md`
— sépare explicitement ses démonstrations des preuves. Un fil rouge qui viendrait remplir
les canevas ferait exactement ce que ces deux décisions interdisent.

Le fil rouge sert donc la méthode. La méthode ne sert pas le fil rouge.

---

## 2. Choix du cas

Le cas retenu s'appelle **TechAtelier**. Il est entièrement fictif.

| Caractéristique | Description |
|---|---|
| Nature | Petite structure de services, quelques personnes, aucun secteur réel |
| Périmètre IT | Un poste de travail, deux machines virtuelles, un stockage partagé |
| Réseau | Un réseau local de documentation, un accès distant maîtrisé |
| Sauvegardes | Une politique déclarée, une restauration jamais testée |
| Incidents | Un historique incomplet, deux incidents mal documentés |
| Documentation | Partielle : quelques notes, aucune procédure reproductible |
| Profil | Un technicien autodidacte en cours de structuration |

Trois lignes suffisent à le situer, et c'est un choix délibéré : un cas décrit en un
paragraphe se prête à la méthode ; un cas détaillé en vingt devient une histoire, et
l'histoire prend le pas sur la démonstration.

Contraintes de conception :

- aucun nom d'organisation réelle ;
- aucun client réel, aucun fournisseur nommé ;
- aucune adresse IP, aucune URL externe, aucun identifiant ;
- aucune configuration exploitable en l'état ;
- aucun secteur économique identifiable.

---

## 3. Ce que le fil rouge ne doit pas devenir

Une section anti-dérive vaut mieux qu'un avertissement oublié.

**Il ne doit pas :**

- devenir un roman, ni un récit chronologique ;
- devenir un cas d'entreprise complexe, avec des dizaines de composants et de sigles ;
- devenir une preuve de compétence, pour le lecteur comme pour l'auteur ;
- pré-remplir un canevas principal, ni en partie ;
- introduire un statut nouveau, ni un marqueur nouveau ;
- présenter une étape supplémentaire à la boucle normative ;
- devenir un parcours commercial, ni porter de promesse ;
- transformer le livre en étude de cas unique ;
- masquer une limite derrière la cohérence d'un récit ;
- servir d'exemple à copier-coller dans un dossier réel.

Le test de dérive le plus simple : si le lecteur peut recopier le fil rouge dans son
propre dossier sans avoir rien fait, le fil rouge a envahi le canevas.

---

## 4. Périmètre par partie

| Partie | Apport du fil rouge | Limite à respecter |
|---|---|---|
| `00_POSITIONNEMENT.md` | Présenter le cas comme illustration de méthode | Ne pas remplacer le mode d'emploi |
| `01_SE_POSITIONNER.md` | Montrer un poste IT générique | Ne pas définir le poste du lecteur |
| `02_SOCLE_TECHNIQUE.md` | Fournir un socle technique fictif et simple | Ne pas transformer le chapitre en cours technique |
| `03_ENVIRONNEMENT_CONTRAINT.md` | Introduire des contraintes réalistes | Ne pas inventer des incidents spectaculaires |
| `04_CONSTRUIRE_SES_PREUVES.md` | Montrer comment un artefact devient preuve potentielle | Ne pas pré-remplir la matrice du lecteur |
| `05_DISCOURS_ENTRETIEN.md` | Fournir un exemple d'explication structurée | Ne pas écrire le discours du lecteur |
| `06_SIMULATION.md` | Proposer une mise en situation finale | Ne pas devenir un corrigé universel |

Le fil rouge est **accompagnateur**, jamais principal. Dans chaque partie, il occupe une
place comparable à celle d'un encadré, pas celle d'une section.

---

## 5. Livrables attendus du fil rouge

Sept livrables, tous présentés comme des **modèles de raisonnement** et jamais comme des
preuves acquises :

| # | Livrable | Rôle |
|---|---|---|
| L1 | Carte du système fictif | Situer le périmètre d'un coup d'œil |
| L2 | Liste des responsabilités du profil fictif | Matière première de la partie I |
| L3 | Socle technique en quatre couches | Matière première de la partie II |
| L4 | Note de décision sous contrainte | Matière première de la partie III |
| L5 | Preuve potentielle structurée | Matière première de la partie IV |
| L6 | Fiche d'explication professionnelle | Matière première de la partie V |
| L7 | Simulation finale | Matière première de la partie VI |

Les quatre couches du socle sont celles du corpus : matériel et ressources, système,
services, utilisateur et métier.

Chaque livrable est un modèle. Un modèle montre la forme d'un raisonnement, il ne
contient pas le raisonnement du lecteur.

---

## 6. Articulation avec la boucle à six temps

Le fil rouge s'inscrit dans la boucle normative du livre :

```
COMPRENDRE → PRATIQUER → VÉRIFIER → PRODUIRE UNE PREUVE
→ EXPLIQUER → IDENTIFIER UNE LIMITE
→ (progression)
```

La progression est l'issue du cycle, puis le point de départ du suivant. Ce n'est pas une
septième étape.

| Temps de la boucle | Ce que le fil rouge montre |
|---|---|
| Comprendre | Le contexte fictif, ses contraintes, ses zones d'ombre |
| Pratiquer | Une action exécutée dans le cas, jamais dans le système du lecteur |
| Vérifier | Un résultat observé, par une seconde voie |
| Produire une preuve | Un artefact qui pourrait devenir preuve, dans le périmètre du cas |
| Expliquer | Le choix effectué et son alternative écartée |
| Identifier une limite | Ce que le cas ne démontre pas |
| (progression) | Ce que le cas prépare, sans le réaliser |

Le fil rouge ne se déroule donc pas une fois : il se parcourt six fois, sur six livrables.

---

## 7. Articulation avec les statuts

Le fil rouge utilise les cinq statuts existants, sans en créer aucun. Un statut attribué
au fil rouge décrit l'état du cas de conception, pas la compétence du lecteur.

| Statut | Dans le fil rouge |
|---|---|
| `OBJECTIF` | Compétence visée par le cas, encore sans preuve |
| `DÉCLARÉ` | Ce que le cas affirme sans l'avoir observé |
| `INTERPRÉTÉ` | Ce qui est déduit de plusieurs observations du cas |
| `DÉMONTRÉ` | Ce qui serait démontré si les vérifications indiquées étaient réellement exécutées |
| `NON ÉTABLI` | Ce que le cas ne parvient pas à établir, et le dit |

Le point délicat est `DÉMONTRÉ`. Dans un scénario pédagogique, il décrit une condition
de démonstration réunie **dans le cas**, jamais une compétence acquise par celui qui lit.
La formulation employée dans le corpus pour cela reste la référence : « état simulé ».

Un statut du fil rouge ne se transcrit jamais tel quel dans la matrice du lecteur. La
matrice ne contient que des statuts issus du dossier réel.

---

## 8. Articulation avec les marqueurs

| Marqueur | Usage dans le fil rouge |
|---|---|
| `OBS` | Ce qui est observé dans le cas, et qui pourrait l'être aussi dans un dossier réel |
| `DÉD` | Ce qui est déduit de plusieurs observations, avec la déduction nommée |
| `N.D.` | Ce qui manque, ou ce qui ne peut pas être montré dans un cas pédagogique |
| `BLOQUÉ` | Dépendance externe du cas, absence de décision, de moyens ou de permission |
| `ÉCHEC` | Tentative non concluante dans le scénario, dont la trace fait partie de la leçon |

Un usage mérite d'être conservé : le `N.D.` du fil rouge sert indifféremment à ce qui
manque et à ce qui ne peut pas être détaillé. Les deux cas se distinguent dans la phrase,
jamais dans le marqueur seul.

---

## 9. Points d'insertion futurs

| Fichier | Point d'insertion possible | Nature de l'insertion |
|---|---|---|
| `00_POSITIONNEMENT.md` | Après le cap éditorial, ou en clôture | Mention courte du cas pédagogique |
| `01_SE_POSITIONNER.md` | Introduction de la partie | Encadré « cas TechAtelier » |
| `02_SOCLE_TECHNIQUE.md` | Début de chaque couche | Périmètre fictif du cas |
| `03_ENVIRONNEMENT_CONTRAINT.md` | Ouverture des exercices | Contraintes génériques du cas |
| `04_CONSTRUIRE_SES_PREUVES.md` | Avant les canevas | Transformation artefact → preuve potentielle |
| `05_DISCOURS_ENTRETIEN.md` | Modèle d'explication | Fiche d'exemple non personnalisée |
| `06_SIMULATION.md` | Avant le scénario final | Énoncé du cas appliqué |

Trois règles pour ces insertions futures :

- elles restent courtes, et balisées par un repère visuel constant ;
- elles ne touchent jamais un canevas, ni même partiellement ;
- elles ne modifient ni le diagramme de la boucle, ni les tableaux de statuts et de
  marqueurs, ni les définitions normatives.

Le repère visuel recommandé reprend la forme du bloc déjà présente dans le corpus : une
sous-titre suivie d'un encadré cité, en trois lignes au plus.

---

## 10. Critères de non-régression pour l'intégration future

Ces critères devront être vérifiés, commande par commande, à chaque mandat d'intégration :

- aucun canevas principal pré-rempli ;
- aucune étape supplémentaire à la boucle ; la boucle reste à six temps, avec
  (progression) comme issue ;
- boucle à six temps inchangée dans les trois diagrammes ;
- cinq statuts inchangés ;
- cinq marqueurs inchangés ;
- aucun statut ni marqueur inventé ;
- aucun registre commercial ;
- aucune donnée sensible réelle ;
- aucune adresse IP hors documentation ;
- aucun message électronique, aucun nom de domaine réel ;
- fil rouge explicitement étiqueté comme pédagogique à chaque occurrence ;
- canevas toujours vides après intégration ;
- si une annexe est créée, `README.md` raccordé dans le même mandat.

Le point le plus fragile est le troisième : c'est lui que l'audit pré-push a rattrapé
sur `05_DISCOURS_ENTRETIEN.md`. Toute intégration du fil rouge devra refaire un contrôle
global, pas un contrôle fichier par fichier.

---

## 11. Arbitrages à préparer

Ces décisions ne sont pas tranchées ici, parce qu'elles touchent au corps du livre ou à
son identité.

1. Nom du cas : `TechAtelier`, ou autre formulation.
2. Niveau de détail : minimal, moyen, soutenu.
3. Présence dans `00_POSITIONNEMENT.md` : mention simple, encadré, ou annexe seule.
4. Forme dans les parties : encadré court, ou section dédiée à la fin de chaque partie.
5. Créer, ou non, une annexe d'exemples remplis séparée du fil rouge.
6. Relier, ou non, le fil rouge à `EXEMPLES_PEDAGOGIQUES.md`.
7. Relier, ou non, le fil rouge à `PARCOURS_PROGRESSION.md`.
8. Relier, ou non, le fil rouge à `ETHIQUE_SECURITE.md` pour la diffusabilité du cas.
9. Ordre d'intégration : parties dans l'ordre du livre, ou parties les plus porteuses
   d'abord.

Aucune de ces décisions ne peut être prise dans le cadre d'un document de conception.

---

## 12. Limite de ce fichier

Ce fichier conçoit un fil rouge.

Il ne l'intègre pas.

Il ne remplace pas le travail du lecteur.

Il ne constitue pas une preuve de compétence.

Toute insertion future devra être validée séparément, mandat par mandat, partie par
partie, sans modifier les canevas vides ni la boucle à six temps.
