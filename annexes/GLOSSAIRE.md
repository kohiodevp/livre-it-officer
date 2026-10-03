# Glossaire

Termes employés dans le livre. Les définitions sont volontairement **courtes et
opérationnelles** : elles décrivent l'usage dans ce livre, pas la spécification
complète de la technologie.

Quand un terme est une **clé douteuse**, cela signifie qu'il est fréquemment
confondu avec un autre — et que la confusion produit des erreurs d'analyse.

---

## A

**Artefact** — Élément produit ou conservé : fichier, configuration, script,
sortie de commande, test, dépôt. Un artefact n'est pas automatiquement une preuve
de compétence ; il faut savoir *ce qu'il permet exactement d'établir*.

**Auto-évaluation** — Retour réflexif sur son propre travail : ce que j'ai réussi,
observé, vérifié, ce qui a échoué, ce que je n'ai pas pu établir, ce que je
refais autrement. Partie VI § 31.

**Autodidacte** — Apprenant qui construit ses compétences par la pratique, la
recherche et la résolution de problèmes, sans cursus structuré. N'est pas
synonyme d'amateur.

---

---

## C

**Canevas** — Bloc de champs à remplir dans le livre. Volontairement vide : une
case vide est une instruction, pas un défaut de rédaction.

**Chaîne diagnostique** — Ordre de vérification du bas vers le haut : `processus →
service → port → protocole → application`. Respecter cet ordre évite de modifier
simultanément plusieurs éléments.

**Compromis** — Ce qu'un choix technique accepte de perdre pour gagner autre chose.
Un choix sans compromis déclaré n'est pas encore expliqué.

**Contrainte** — Limite réelle de l'environnement : ressource finie, réseau
intermittent, absence d'Internet, délai de maintenance. La contrainte n'est pas
l'ennemie de l'apprentissage — elle oblige à raisonner, et à distinguer le
fonctionnement local de la dépendance externe.

**Compétence** — Ce que l'on sait comprendre, réaliser, raisonner ou expliquer dans
un contexte professionnel. Une compétence peut être réelle et rester
indémontrable.


---

## D

**DÉCLARÉ** — Statut : l'information est affirmée par une documentation, mais la
preuve opérationnelle n'a pas été observée.

**DÉD** — Marqueur de travail : contenu déduit, paragraphe ou cas de figure. À ne
pas confondre avec INTERPRÉTÉ.

**DÉMONTRÉ** — Statut : une preuve vérifiable, issue d'une exécution constatée, établit le résultat ou la compétence dans le périmètre considéré. Un artefact non exécuté n'atteint jamais ce statut : il reste DÉCLARÉ..

**Déploiement** — Action de rendre un système opérationnel sur une cible réelle.
Distinguable d'une configuration déclarée, qui n'est qu'un fichier.

**Diagnostic** — Démarche qui va du symptôme à la cause, en isolant la couche
responsable avant d'agir. Partie II § 16.

---

## E

**ÉCHEC** — Marqueur de travail : contenu qui n'a pas pu être établi malgré une
tentative. Décrit un obstacle documentaire, pas une insuffisance personnelle.

**État initial** — Photographie de l'état d'un système **avant** toute intervention.
C'est la référence de comparaison qui rend possible un « après » interprétable.
Sans état initial documenté et daté, aucune conclusion sur l'effet d'une action
n'est défendable.

---

## G

**Grille d'observation** — Tableau de critères observables permettant d'évaluer
une simulation sur des comportements, non sur des impressions. Partie VI § 29.

---

## I

**INTERPRÉTÉ** — Statut : conclusion raisonnable tirée d'éléments observés, qui
dépasse ce qui est directement démontré. Ne doit jamais être présentée comme un
fait.

---

## L

**Limite** — Ce qui n'a pas été établi, nommé explicitement. Ce n'est pas un échec :
c'est une information qui oriente la progression suivante. Le sixième temps de la
boucle.

**Liste blanche** — Ensemble de valeurs autorisées, par opposition à une liste
noire de valeurs rejetées. `set -euo pipefail` relève de la logique en liste
blanche.

---

## M

**Marqueur de travail** — `OBS`, `DÉD`, `N.D.`, `BLOQUÉ`, `ÉCHEC`. Décrit l'état
d'un **texte**, jamais la valeur probante d'un résultat.

**Matrice de preuves** — Tableau qui relie chaque compétence à sa source, son
observable, son statut et la formulation autorisée. Voir
[`MATRICE_PREUVES.md`](./MATRICE_PREUVES.md).

---

## N

**N.D.** — Marqueur de travail : information non disponible, à produire. Utilisé
quand l'information n'est pas dans le périmètre consulté.

**NON ÉTABLI** — Statut : les éléments disponibles ne permettent pas de conclure.
Ne signifie pas que la compétence n'existe pas.

---

## O

**OBJECTIF** — Statut : compétence ou pratique visée mais pas encore acquise ni
démontrée. Voir [`OBJECTIFS_A_COMPLETER.md`](./OBJECTIFS_A_COMPLETER.md).

**Observable** — Ce qui peut être constaté par une commande ou un fichier. Dans la
matrice, la deuxième colonne.

---

## P

**Passation** — Transmission d'un travail à un tiers qui n'a pas la mémoire du
projet. C'est le test le plus sévère de la qualité documentaire.

**Preuve** — Élément qui permet d'établir une compétence selon un critère défini :
artefact, sortie, test, démonstration, documentation, compte rendu.

**Preuve minimale utile** — Preuve contenant contexte, action, observation,
résultat, date et limite — sans être volumineuse. Partie IV § 13.

---

## Q

**Qualification** — Attribution d'un statut à une compétence, après examen des
preuves disponibles. Ne jamais la remplir par anticipation.

---

## R

**Reproductibilité** — Capacité à refaire une opération dans les mêmes conditions
et à obtenir le même résultat. Une preuve historique ne la garantit pas.

**Revue par les pairs** — Présentation du travail à un autre IT pour tester sa
compréhension. L'objectif n'est pas de défendre son code à tout prix.

---

## S

**STAR+** — Structure de récit : Situation, Tâche, Action, Résultat, **plus** la
Limite et l'Apprentissage. Le « + » empêche le récit de s'arrêter au résultat
déclaré.

**Statut** — Qualification d'une preuve : DÉMONTRÉ, DÉCLARÉ, INTERPRÉTÉ,
OBJECTIF, NON ÉTABLI.

**Système de fichiers** — Arborescence et permissions. La distinction
**propriétaire / groupe / autres** et **lecture / écriture / exécution** est la
base de toute administration de permissions.

---

## T

**Test de restauration** — Vérification qu'une sauvegarde peut effectivement être
récupérée. Une sauvegarde non restaurée reste une **hypothèse opérationnelle**.

**Trace d'exécution** — Sortie conservée d'une commande, avec sa date, son
environnement et son code de retour.

---

## V

**VLAN** — Segmentation logique du réseau. Séparation par identifiant, pas par
câblage. Partie II § 5.2.

**Vérification** — Observation qui confirme ou écarte une hypothèse. Une
vérification absente laisse l'hypothèse au même statut qu'avant.

---

## Termes volontairement absents

Les technologies sans pratique documentée dans le dossier — Windows Server, Active
Directory, SAN/NAS/RAID, ISO 27001, ITIL — **ne sont pas définies ici**. Les
définir reviendrait à leur attribuer un statut qu'elles n'ont pas. Elles figurent
dans [`OBJECTIFS_A_COMPLETER.md`](./OBJECTIFS_A_COMPLETER.md) comme objectifs.