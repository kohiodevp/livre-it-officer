# Exemples pédagogiques

> Ce fichier contient des démonstrations de méthode.
>
> Les situations, artefacts et statuts présentés ici illustrent la boucle des six temps :
>
> ```text
> COMPRENDRE → PRATIQUER → VÉRIFIER → PRODUIRE UNE PREUVE
> → EXPLIQUER → IDENTIFIER UNE LIMITE
> → (progression)
> ```
>
> Ils ne constituent pas des preuves de compétence pour le lecteur.
> Ils ne remplacent pas les canevas vides des parties principales.
> Ils servent uniquement à montrer comment une pratique déclarée peut être structurée,
> vérifiée, limitée et rendue défendable.

---

## Mode d'emploi de ce fichier

Trois exemples sont proposés : sauvegarde et restauration, réseau et connectivité,
incident et décision sous contrainte. Ils couvrent trois profils courants — support,
administration système, réseau — et trois natures d'artefacts : un script, une
capture, un récit.

Chaque exemple suit la même progression :

```
1. Situation initiale      ce que l'on raconte spontanément
2. Artefact brut           ce que l'on présente comme preuve
3. Ce que l'artefact ne prouve pas
4. Application de la boucle   les six temps, un par un
5. Version structurée     le même contenu, réorganisé
6. Limite de cet exemple
7. Prochaine action        issue : (progression)
```

### Trois précisions de lecture

**Sur les statuts.** Les statuts utilisés ci-dessous décrivent l'état d'un raisonnement
d'exemple, jamais la valeur probante d'un dossier réel. Lorsqu'un exemple indique
« DÉMONTRÉ », il s'agit d'un état **simulé** : la condition de démonstration serait
réunie *si* les vérifications indiquées étaient réellement exécutées. Aucun de ces
exemples n'attribue une compétence à celui qui les lit.

**Sur la formule à sept verbes.** Le manifeste emploie une formule en sept verbes —
se comprend, se pratique, se vérifie, se prouve, s'explique, se limite et progresse.
Elle décrit un mouvement global. Elle n'ajoute pas de septième temps à la boucle : la
progression reste une issue.

**Sur les marqueurs.** Les marqueurs de travail distinguent l'état d'une information,
pas sa valeur probante :

| Marqueur | Signification |
|---|---|
| `OBS` | Contenu observé et vérifiable en l'état |
| `DÉD` | Contenu déduit |
| `N.D.` | Information non disponible — à produire |
| `BLOQUÉ` | Dépend d'une preuve ou d'une décision externe |
| `ÉCHEC` | N'a pas pu être établi malgré une tentative |

### Genericisation des exemples

Tous les noms, adresses et chemins sont fictifs. Les adresses employées appartiennent
à des plages réservées à la documentation (RFC 5737) et ne pointent vers aucune
machine. Aucun nom d'organisation, aucun identifiant réel, aucune donnée personnelle,
aucune donnée sensible ne figure dans ce fichier.

---

## Exemple 1 — Du script de sauvegarde à la preuve potentielle

### Situation initiale

> J'ai un script `backup.sh` qui copie les fichiers importants.

C'est la formulation la plus fréquente. Elle est vraie, et elle ne prouve presque rien.

### Artefact brut

Script `backup.sh` présent dans un dépôt de code, lisible, commenté.

### Ce que l'artefact ne prouve pas

Le fait qu'un script existe n'établit pas :

- que le script a été exécuté ;
- que les fichiers ont été copiés intégralement ;
- que l'intégrité des copies est vérifiée ;
- que la restauration fonctionne ;
- que le périmètre sauvegardé est adapté aux données à protéger ;
- que les droits et les destinataires sont corrects ;
- que les journaux sont conservés ;
- que la procédure est reproductible par un tiers.

Un script de sauvegarde est un **artefact de déclaration d'intention**. Il dit ce que
l'on a prévu de faire. Il ne dit pas ce qui a été fait.

### Application de la boucle

| Temps | Ce que l'on fait dans cet exemple |
|---|---|
| **Comprendre** | Nommer ce que « sauvegarder » signifie : copie, cohérence, rétention, et la différence entre une copie et une restauration |
| **Pratiquer** | Écrire le script, puis l'exécuter sur un environnement de test isolé |
| **Vérifier** | Contrôler le contenu copié, pas seulement le code de retour |
| **Produire une preuve** | Conserver l'exécution horodatée, le journal, les sommes de contrôle et un test de restauration |
| **Expliquer** | Dire pourquoi ce périmètre, cette rétention, et ce que le script ne couvre pas |
| **Identifier une limite** | Nommer ce qui n'a pas été testé : liens symboliques, fichiers ouverts, permissions, chiffrement |

### Version structurée de la preuve potentielle

```
Contexte            : poste de travail vm-test, données de projet fictives
Périmètre           : /srv/DonneesExemples, 1 arborescence, droits 0640
Artefact            : script backup.sh, versionné, relu
Exécution observée  : à horodater — sortie conservée dans journal-exemple.log
Sortie / journal    : fichiers copiés, octets, horodatage par entrée
Vérification        : comparaison des sommes de contrôle source / copie
Intégrité           : somme SHA-256 du manifeste avant et après copie
Test de restauration : à produire — restauration sur vm-test-2, puis lecture
Limite              : liens symboliques, fichiers ouverts et chiffrement non traités
Statut simulé       : DÉCLARÉ au départ
                      INTERPRÉTÉ après exécution seule
                      DÉMONTRÉ seulement si le test de restauration est réussi
                      et consigné, dans le périmètre indiqué
```

Le mot `potentiellement` est déterminant. Tant que la ligne « test de restauration »
est vide, le statut reste en deçà du seuil de la démonstration.

### Limite de cet exemple

Cet exemple illustre une structuration possible. Il ne prouve pas que le lecteur a
réalisé une sauvegarde fiable. Il ne remplace pas un test de restauration horodaté,
un contrôle d'intégrité et une revue du périmètre.

Il ne préjuge pas non plus du fait qu'un script de restauration réel soit correct :
un scénario pédagogique décrit un raisonnement, pas une exécution.

### Prochaine action

Produire une restauration testée sur un environnement isolé, avec journal horodaté,
contrôle d'intégrité et périmètre explicite.

Issue : (progression)

---

## Exemple 2 — Du ping réussi au diagnostic réseau contextualisé

### Situation initiale

> Je connais le réseau, j'ai fait un ping qui passe.

Le ping est l'artefact réseau le plus diffusé et le plus surinterprété.

### Artefact brut

Capture d'écran d'un `ping` réussi vers une adresse.

### Ce que l'artefact ne prouve pas

Un `ping` réussi n'établit pas :

- que la route par défaut est correcte ;
- que la résolution DNS fonctionne ;
- que le pare-feu autorise le service applicatif ;
- que la latence est acceptable pour l'usage concerné ;
- que le problème est résolu de façon durable ;
- que le test a parcouru le bon chemin réseau ;
- que le test a couvert la bonne couche ;
- que l'observation est reproductible par un tiers.

Un `ping` prouve une **reachabilité ICMP à un instant donné**. Il ne prouve ni une
maîtrise du routage, ni une disponibilité de service, ni une compétence réseau.

### Application de la boucle

| Temps | Ce que l'on fait dans cet exemple |
|---|---|
| **Comprendre** | Distinguer les couches : lien, réseau, transport, application. Un `ping` ne teste que l'une d'elles |
| **Pratiquer** | Rejouer le test depuis le poste concerné, puis depuis un second point |
| **Vérifier** | Croiser plusieurs observations au lieu de conclure sur une seule |
| **Produire une preuve** | Conserver les sorties horodatées, la commande exacte et le contexte réseau |
| **Expliquer** | Dire quel chemin a été emprunté, ce qui répond, et ce qui ne répond pas |
| **Identifier une limite** | Nommer la couche non testée et l'hypothèse qui reste ouverte |

### Version structurée de la preuve potentielle

```
Symptôme observé      : un service applicatif est injoignable depuis vm-test
Périmètre testé       : réseau local 192.0.2.0/24, machine 192.0.2.10 (plage de documentation)
Commandes utilisées   : ping -c 4, ip route show, traceroute, getent hosts,
                         puis test du port applicatif
Sorties conservées    : horodatées, une par commande, dans réseau-exemple/
Interprétation        : ce que chaque sortie autorise à dire, et rien de plus
Déductions           : uniquement à partir de plusieurs observations concordantes
Vérification complémentaire : le service répond-il sur son port, depuis un autre point ?
Limite               : l'ICMP ne renseigne ni le DNS applicatif, ni le filtrage,
                         ni la disponibilité de la couche applicative
Statut simulé        : OBS sur les sorties ; DÉD sur la topologie ;
                         N.D. sur la résolution de nom et le port applicatif
```

### Distinction observation / déduction

C'est le cœur pédagogique de cet exemple :

```
OBS : ping vers 192.0.2.10 réussi, 0 % de perte sur 4 paquets
DÉD : la connectivité ICMP fonctionne probablement au niveau du réseau local
N.D. : la résolution DNS du service applicatif n'a pas été vérifiée
N.D. : l'existence d'une route de retour n'a pas été contrôlée
BLOQUÉ : la politique de pare-feu est inaccessible depuis ce poste
```

Les adresses `192.0.2.0/24` sont réservées à la documentation (RFC 5737). Elles ne
désignent aucune machine réelle et le raisonnement reste lisible tel quel.

### Limite de cet exemple

Un ping réussi prouve une reachabilité limitée, pas une compétence réseau complète.
Cet exemple ne valide ni le routage complet, ni la résolution DNS, ni la politique de
pare-feu, ni la disponibilité applicative.

La mention `BLOQUÉ` ci-dessus signale un cas fréquent et important : certaines
informations ne sont pas obtenables depuis le poste de travail. Les pages qui ne sont
pas obtenables se nomment, elles ne s'inventent pas.

### Prochaine action

Compléter avec `ip route show`, `traceroute`, résolution DNS, test du port cible, et
conservation des sorties horodatées.

Issue : (progression)

---

## Exemple 3 — De l'incident résolu à la décision documentée sous contrainte

### Situation initiale

> J'ai géré un incident critique, j'ai tout remis en service.

C'est la situation la plus difficile à prouver, parce que l'urgence qui l'a produite
est précisément ce qui empêche la documentation.

### Artefact brut

Récit oral, ou ticket clos avec une résolution en deux lignes.

### Ce que l'artefact ne prouve pas

Un incident « résolu » n'établit pas :

- la chronologie réelle des événements ;
- l'impact mesuré sur les utilisateurs ;
- la cause racine, seulement la cause probable ;
- les actions réellement entreprises et leur ordre ;
- les vérifications de retour à la normale ;
- les risques résiduels assumés ;
- les décisions prises sous contrainte et leurs alternatives écartées ;
- la communication faite aux parties prenantes ;
- la possibilité de reproduire ou de prévenir l'incident.

Un récit d'incident est un **artefact de mémoire**. Il devient une preuve lorsqu'il est
transformé en note de décision horodatée, vérifiable et revue.

### Application de la boucle

| Temps | Ce que l'on fait dans cet exemple |
|---|---|
| **Comprendre** | Distinguer symptôme, cause probable et cause racine. Les trois ne se confondent pas dans un compte rendu |
| **Pratiquer** | Prendre l'habitude de noter pendant l'incident, pas après — sous contrainte de temps |
| **Vérifier** | Revenir sur la chronologie avec les journaux, pas avec le souvenir |
| **Produire une preuve** | Note de décision : contexte, impact, hypothèses, option retenue, action, vérification, limite |
| **Expliquer** | Justifier l'option retenue au regard de la contrainte, y compris ce qui a été sacrifié |
| **Identifier une limite** | Nommer ce qui reste inconnu : cause racine non confirmée, angle mort de supervision |

### Version structurée de la preuve potentielle

```
Contexte        : service interne fictif, hors production réelle, usage pédagogique
Déclencheur     : signalement d'indisponibilité
Impact observé : indisponibilité de 14 minutes selon les journaux de l'exemple
Contrainte      : restauration de service avant investigation complète
Hypothèses      : au moins trois, dont saturation disque et dépendance réseau
Décision        : action de restauration retenue, investigation différée
Action          : intervention sur vm-test, journal conservé
Vérification    : test de service après intervention, résultat daté
Preuve conservée: journal horodaté, sortie de commande, note de décision
Communication   : information au responsable avec l'état réel et les inconnues
Limite          : cause racine non confirmée, fenêtre de supervision incomplète
Action préventive : à produire — corrélation espace disque et saturation
Statut simulé   : DÉCLARÉ sur la chronologie au départ ; INTERPRÉTÉ sur la cause
                  DÉMONTRÉ seulement si la chronologie est reconstruite depuis les
                  journaux et la vérification de retour à la normale est consignée
```

### Distinction observation / déduction

```
OBS : service indisponible pendant 14 minutes selon le journal horodaté
DÉD : la cause probable est une saturation du disque système
N.D. : cause racine non confirmée par lecture du journal complet
ÉCHEC : la vérification de l'espace disque au moment de l'incident n'a pas pu être
        rejouée après le redémarrage — l'état avait changé
```

Le marqueur `ÉCHEC` mérite une note. Un échec de vérification n'est pas un défaut à
masquer : c'est une information qui borne ce qui peut être affirmé. Le livre le
prévoit à ce titre.

### Limite de cet exemple

Cet exemple montre comment structurer un retour d'incident. Il ne prouve pas que le
lecteur a conduit une gestion d'incident professionnelle. Il ne remplace pas une
timeline vérifiée, des journaux conservés, une revue par les pairs et une action
préventive suivie.

Les durées et volumétries citées sont inventées pour la démonstration. Aucune donnée
d'incident réelle n'est reproduite ici.

### Prochaine action

Transformer le récit en note de décision : contexte, contrainte, risque, option
retenue, vérification, preuve, limite, prévention.

Issue : (progression)

---

## Ce que ces trois exemples ne font pas

Ils ne remplissent aucun canevas des parties I à VI. Ces canevas appartiennent au
lecteur, et le livre les laisse vides par choix méthodologique : une expérience supposée
n'a pas de valeur de preuve.

Ils ne constituent pas non plus un modèle de dossier réel. Un dossier réel contient des
pièces que ces exemples n'ont pas : horodatage fiable, identité du contexte,
traçabilité, anonymisation vérifiée, relecture par un tiers. Le lecteur qui souhaite
produire un tel dossier trouvera dans la partie IV les instruments correspondants.

Ces exemples montrent une méthode. Ils ne Livrent pas un résultat. La différence entre
les deux est exactement l'objet du livre.
