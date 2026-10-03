# ÉTHIQUE ET SÉCURITÉ DES PREUVES IT

> Ce fichier fixe des règles de prudence professionnelle.
>
> Il ne constitue pas un avis juridique.
> Il ne remplace pas une revue de sécurité, une validation hiérarchique
> ou une conformité interne.
>
> Son objet est d'éviter qu'une preuve technique devienne un risque
> organisationnel, juridique ou sécuritaire.

---

## 1. Principe cardinal

**Produire une preuve ne dispense pas de protéger le système, les données et les
personnes concernées.**

Le livre enseigne à conserver des artefacts, à les contextualiser, à les nommer, à
leur attribuer une limite. Cet enseignement a un corollaire : une preuve est une donnée
comme une autre.
Elle peut contenir une information que l'organisation a décidé de ne pas diffuser.

Ce corollaire ne s'oppose pas à la méthode, il la complète. Une preuve qui expose le
système qu'elle prétend documenter a produit un dommage au lieu d'une compétence
démontrée.

Le livre traite déjà les secrets comme un sujet d'exploitation — ne pas les mélanger au
code source, limiter les services exposés, éviter toute modification hors périmètre. La
section qui suit porte sur une autre question : ce que l'on peut **partager** une fois le
travail fait.

---

## 2. Un statut ne vaut que dans son périmètre

Le statut `DÉMONTRÉ` décrit un fait observé dans un périmètre donné. Il ne décrit pas une
valeur de partage.

Trois distinctions doivent rester séparées :

```
DÉMONTRÉ en interne ≠ publiable externement
DÉMONTRÉ sur un système de production ≠ transmissible sans autorisation
DÉMONTRÉ dans un laboratoire ≠ représentatif d'un environnement client
```

Un artefact peut être pleinement établi — exécution observée, sortie conservée, limite
nommée — et rester non diffusable. Ces deux jugements ne s'annulent pas : ils portent sur
deux objets différents, l'un sur la validité technique, l'autre sur le droit de
transmettre.

C'est la même règle que la distinction entre preuve et artefact, appliquée un cran plus
loin : une preuve établit un fait, elle n'ouvre aucun droit de diffusion.

---

## 3. Données sensibles à ne pas exposer

Les catégories suivantes ne doivent pas figurer dans une preuve partagée, sauf
autorisation explicite et traitement approprié.

**Identifiants et éléments cryptographiques**

- mots de passe, quelle que soit leur forme de stockage ;
- jetons d'authentification, de session ou d'API ;
- clés privées, tous algorithmes ;
- certificats et clés de chiffrement applicatif ;
- fichiers d'environnement contenant des valeurs ;
- identifiants de service et comptes techniques ;
- clés de récupération, codes d'authentification.

**Données d'organisation et de tiers**

- données personnelles, en ce qu'elles identifient ou caractérisent une personne ;
- identifiants de clients, de fournisseurs, d'utilisateurs ;
- topologies réseau internes non publiées ;
- adresses et noms d'hôtes internes ;
- tickets, comptes rendus d'incident et discussions internes ;
- configurations et procédures internes non autorisées à la diffusion.

**Faiblesses exploitables**

- vulnérabilités non corrigées, décrites de manière exploitable ;
- preuves de concept fonctionnelles ;
- procédures d'intrusion exécutables ;
- mécanismes d'authentification contournés, en description opératoire.

**Captures et journaux**

- captures d'écran contenant une session ouverte ou des données personnelles ;
- journaux bruts comportant des noms, adresses ou identifiants ;
- dumps de bases de données, même partiels ;
- métriques internes non publiques.

Ces catégories sont nommées ici comme **catégories**, jamais par des valeurs. Aucun
exemple réel n'est reproduit dans ce fichier.

---

## 4. Anonymiser sans détruire la preuve

**Une preuve peut être utile sans être exhaustive.**

La question à poser n'est pas « comment masquer ce que je montre », mais « quelle partie
suffit à établir le fait que je prétends démontrer ».

Méthodes disponibles, de la plus intrusive à la moins intrusive :

| Méthode | Effet | Ce qu'elle préserve | Ce qu'elle détruit |
|---|---|---|---|
| Extraction de structure | ne garder que le schéma, la forme, la séquence | la logique du fonctionnement | tout contenu |
| Reproduction isolée | rejouer le cas dans un environnement reconstruit | le mécanisme | l'empreinte du système réel |
| Agrégation | remplacer les valeurs par des fourchettes ou des totaux | l'ordre de grandeur | la valeur unitaire |
| Troncature | ne garder que l'extrait nécessaire | la preuve ciblée | la continuité |
| Masquage | remplacer un identifiant par un jeton stable | la correspondance entre deux sorties | l'identification |
| Substitution | remplacer par une valeur fictive cohérente | la lisibilité | toute valeur réelle |
| Hachage | remplacer par une empreinte non réversible | la preuve d'égalité | la comparaison visuelle |

Le hachage a une limite qu'il faut connaître : il prouve que deux valeurs sont identiques,
pas qu'une valeur est correcte. Il ne remplace pas une validation.

Règle de décision, dans cet ordre :

1. Quelle est l'affirmation que je cherche à soutenir ?
2. Quel est l'élément minimal qui la soutient ?
3. Ce retrait détruit-il la vérifiabilité pour un tiers ?
4. Si oui, le système peut-il être reproduit isolément ?
5. Si non, l'affirmation est peut-être trop large.

La dernière question est la plus utile : un artefact qu'on ne peut pas anonymiser sans le
rendre inintelligible signifie souvent qu'on démontre une chose trop large.

---

## 5. Adapter la preuve au destinataire

**Le même artefact n'a pas la même valeur de partage selon le destinataire.**

| Destinataire | Ce qu'il attend | Ce que la preuve doit contenir |
|---|---|---|
| soi-même | le dossier de travail complet | artefacts bruts, journaux, essais échoués |
| équipe technique | le détail vérifiable | commandes, sorties, environnement de test |
| pair technique | la discussion des choix | périmètre, méthode, limites assumées |
| responsable hiérarchique | la synthèse et la décision | résultat, périmètre, conséquences |
| auditeur interne | la traçabilité | horodatage, périmètre, autorisations, journal |
| recruteur | la compétence et sa limite | méthode, résultat, limite — sans détail sensible |
| client | la conformité de service | engagements tenus, périmètre couvert |
| public | la leçon transférable | mécanisme générique, sans système identifiable |

Deux fautes symétriques se font face.

La première consiste à montrer la version brute à un public : la crédibilité augmente
puis disparaît, parce que le lecteur conclut que la compétence à documenter est elle-même
faible.

La seconde consiste à montrer une version tellement édulcorée que rien n'est vérifiable :
le dossier ne prouve plus rien, et il perd sa raison d'être.

Le bon niveau de détail est celui qui permet **un doute compétent** — c'est-à-dire un
le lecteur, au lieu de seulement comparer, pourrait vérifier

---

## 6. Autorisation, propriété et confidentialité

**Une compétence peut être réelle, alors que l'artefact qui la documente ne peut pas être
diffusé.**

Ce désaccord est fréquent et il n'a rien d'anormal. Une partie des preuves d'un
professionnel a été produite sur des systèmes qui appartiennent à d'autres.

Cas à distinguer :

| Nature | Question à se poser |
|---|---|
| Données d'employeur | le système appartient-il à l'organisation qui m'emploie ? |
| Données de client | une relation contractuelle encadre-t-elle la diffusion ? |
| Données personnelles | des personnes sont-elles identifiables ? |
| Savoir-faire d'entreprise | l'artefact révèle-t-il une méthode interne rare ? |
| Propriété intellectuelle | l'artefact est-il produit sous une licence ou une commande ? |
| Politique interne | une règle locale interdit-elle la sortie d'information ? |
| Restriction contractuelle | une clause d'engagement limite-t-elle la publication ? |

Trois réflexes, dans cet ordre :

1. **Vérifier** si une règle s'applique, avant de chercher à diffuser.
2. **Demander** si le doute persiste — l'écrit vaut mieux que l'implicite.
3. **Réduire** par défaut — une preuve réduite reste une preuve, une preuve non
   autorisée reste un risque.

La règle par défaut en cas d'hésitation est donc la réduction du périmètre, pas la
diffusion.

---

## 7. Incidents et vulnérabilités

**Prouver que l'on a sécurisé un système ne consiste pas à exposer comment il pouvait
être compromis.**

Cette section est la plus délicate du fichier, parce que le sujet est à la fois légitime et
facilement détournable.

Lignes de partage :

- **Ce qui est partageable** — que le problème a été détecté, ce qui a été changé, ce qui
  a été vérifié après, ce qui reste ouvert.
- **Ce qui ne l'est pas** — le vecteur d'exploitation détaillé, la combinaison de
 Versions affectées, la procédure reproductible par un tiers.

Sur un incident, la preuve utile est la **note de décision** : contexte, contrainte,
impact, options écartées, option retenue, vérification, limite, action préventive. Cette
note montre la compétence. Elle n'expose pas la faille.

Sur une vulnérabilité, la séquence indicative est : signalement au responsable, délai de
correction, disclosure coordonnée, publication ensuite. Publier d'abord et prévenir
ensuite n'est pas de la rigueur ; c'est une manière de déplacer une décision qui
n'appartient pas au technicien.

Cet ordre est indicatif. Il doit être adapté à la politique de sécurité de
l'organisation, aux obligations contractuelles applicables et, le cas échéant, à un avis
compétent.

Ce fichier ne se prononce pas sur les obligations légales applicables à une disclosure :
c'est précisément ce que l'avertissement initial exclut. Quand ce point est atteint, la
bonne décision consiste à ne pas publier et à demander un avis.

---

## 8. Articulation avec les statuts

| Statut | Règle de prudence |
|---|---|
| `DÉMONTRÉ` | Vaut dans le périmètre technique observé et dans le périmètre organisationnel autorisé. Au-delà, il redevient `DÉCLARÉ` |
| `DÉCLARÉ` | Ne doit jamais être présenté comme une exécution observée, même si l'artefact est réel |
| `INTERPRÉTÉ` | Doit signaler la part de déduction et le raisonnement qui l'a produite |
| `OBJECTIF` | Ne doit pas être comblé par un artefact obtenu de façon non autorisée |
| `NON ÉTABLI` | Ne doit pas être transformé en preuve par extrapolation ni par narratif |

Trois précisions.

**La rétrogradation est normale.** Un artefact `DÉMONTRÉ` qui sort de son périmètre
autorisé redevient `DÉCLARÉ` pour le destinataire. Ce n'est pas une déclassification de la
compétence ; c'est la prise en compte d'un périmètre nouveau.

**Le partage ne modifie pas le statut.** Réduire un artefact pour le rendre publiable ne
l'améliore pas et ne le dégrade pas : il produit une version adaptée, dont il faut dire
quelle elle est.

**Aucune diffusabilité n'est un statut.** `DÉMONTRÉ` décrit une compétence. La droit de
transmettre décrit une autorisation. Les deux jugements sont orthogonaux, et le livre n'a
besoin d'aucun statut supplémentaire pour les exprimer.

---

## 9. Articulation avec les marqueurs

| Marqueur | Usage prudentiel |
|---|---|
| `OBS` | Observer en neutralisant les données sensibles : ce qui est observé doit pouvoir être montré |
| `DÉD` | Séparer la déduction de l'observation, et signaler ce qui n'est pas une observation |
| `N.D.` | Peut signifier **non disponible** — l'information manque — ou **non divulgable** — elle existe mais ne peut pas être partagée. La distinction se fait dans la phrase |
| `BLOQUÉ` | Peut signaler une dépendance d'autorisation ou de sécurité, autant qu'une dépendance de preuve |
| `ÉCHEC` | Ne se publie pas tel quel s'il contient des données sensibles ; le résultat se décrit sans la charge |

La double lecture de `N.D.` mérite d'être explicite, parce qu'elle est la plus utile en
pratique.Face à un pair technique, `N.D.` pour cause de confidentialité protège le
système sans disqualifier le travail. Face à un auditeur, la même mention doit
contrairement désigner ce qui n'a pas pu être obtenu. Le marqueur ne suffit pas à porter le
sens : la phrase doit le dire.

Écrire par exemple : « le résultat du test reste `N.D.` — la commande a été exécutée, sa
sortie contient des données non partageables dans ce contexte », plutôt que « résultat
`N.D.` ». La première version indique ce qui manque, ce qui existe, et pourquoi.

---

## 10. Checklist avant partage

```markdown
## Checklist avant partage d'une preuve

- [ ] Aucun secret technique n'est exposé.
- [ ] Aucune donnée personnelle n'est présente.
- [ ] Aucun identifiant de client ou de tiers n'est conservé.
- [ ] Le périmètre de la preuve est explicité.
- [ ] Le destinataire est adapté au niveau de détail retenu.
- [ ] L'autorisation nécessaire a été obtenue si le système appartient à un tiers.
- [ ] La preuve ne contient pas d'exploit fonctionnel.
- [ ] Les limites sont déclarées.
- [ ] La version partagée est distinguée de la version interne.
- [ ] La preuve reste vérifiable sans être dangereuse.
```

La dernière case est la plus difficile et la plus utile : si cocher les neuf premières
rend la preuve invérifiable, c'est que l'affirmation est trop large — ou que le système
trop sensible. Les deux se traitent différemment, et le doute doit être nommé.

---

## 11. Limite de ce fichier

Ce fichier fixe des règles de prudence.

Il ne garantit pas la conformité légale.

Il ne remplace pas une revue de sécurité, un avis juridique ou une validation
hiérarchique.

Il ne couvre pas les obligations propres à un secteur, à une juridiction ou à une
organisation : celles-ci existent, sont plus précises que ce document, et doivent être
consultées directement.

En cas de doute sur la diffusabilité d'une preuve, la règle par défaut est l'abstention
ou la réduction du périmètre. Cette règle peut parfois rendre un dossier moins
impressionnant. C'est le coût attendu d'une preuve fiable.
