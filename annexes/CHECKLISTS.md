# Checklists

Aides opérationnelles du livre. Chaque checklist est un **outil de travail** : son
usage ne prouve rien tant que les cases ne sont pas cochées et le résultat
conservé.

**Convention de statut :** une checklist cochée peut passer au statut DÉMONTRÉ si la
preuve correspondante est conservée. Cochée sans preuve, elle reste DÉCLARÉ.

---

## 1. Avant une intervention

*Partie III § 6, Partie VI § 10 — observer avant d'agir*

```
[ ] J'ai reçu la demande et je l'ai reformulée à voix haute
[ ] Je sais ce qui est attendu et ce qui est observé
[ ] J'ai vérifié le périmètre : qu'est-ce qui est autorisé ?
[ ] J'ai le droit d'accès nécessaire (et seulement celui-là)
[ ] J'ai noté l'état initial AVANT toute modification
[ ] J'ai horodaté mon observation
[ ] J'ai identifié les services qui ne doivent pas être interrompus
[ ] J'ai une méthode de retour en arrière connue
```

**Critère de sortie :** l'état initial est écrit et daté. Sans cela, aucune
comparaison n'est possible après l'action.

---

## 2. Diagnostic réseau

*Partie II § 5, Partie VI § 22*

La chaîne, dans l'ordre. **Ne pas sauter d'étape.**

```
[ ] 1 · Interface    — l'interface est-elle UP ?
[ ] 2 · Adressage    — l'adresse est-elle présente et correcte ?
[ ] 3 · Route        — la route vers la destination existe-t-elle ?
[ ] 4 · Résolution   — le nom se résout-il ?
[ ] 5 · Connectivité — la destination répond-elle au ping ?
[ ] 6 · Port         — le port est-il accessible ?
[ ] 7 · Protocole    — le service répond-il au protocole attendu ?
[ ] 8 · Application  — l'application renvoie-t-elle le résultat attendu ?
```

**Règle.** L'étape où la vérification échoue est l'étape responsable. Ne pas
modifier les étapes précédentes.

---

## 3. Vérification d'un service

*Partie II § 4, § 7 — démarrer n'est pas fonctionner*

```
[ ] 1 · Le service existe        (systemctl list-unit-files)
[ ] 2 · Le service est actif    (systemctl status)
[ ] 3 · Le port écoute          (ss -tlnp)
[ ] 4 · Le protocole répond     (curl -I)
[ ] 5 · La réponse est correcte (contenu attendu obtenu)
[ ] 6 · Les journaux sont propres (journalctl, pas d'erreur bloquante)
[ ] 7 · Le comportement est reproductible (relancer et re-vérifier)
[ ] 8 · Aucune régression observée (services voisins)
```

---

## 4. Sécurité d'un service exposé

*Partie II § 6, § 15 — réduire avant de complexifier*

```
[ ] Les ports exposés sont listés et chacun est justifié
[ ] Les interfaces d'administration sont en loopback (127.0.0.1)
[ ] L'accès distant passe par un tunnel, pas par une porte ouverte
[ ] Aucun secret n'est dans le dépôt ni dans la commande
[ ] Les permissions de l'utilisateur de service sont minimales
[ ] Les journaux du service sont conservés et consultés
[ ] La configuration a été relue après modification
```

---

## 5. Sauvegarde et restauration

*Partie II § 7, Partie III § 21, Partie VI § 21*

### Cycle de sauvegarde

```
[ ] Les données critiques sont identifiées
[ ] La fréquence est fixée et justifiée
[ ] La destination est hors de la machine
[ ] Le nombre de copies est défini (3-2-1)
[ ] La rétention est explicite
[ ] La sauvegarde s'exécute sans erreur
[ ] L'intégrité est vérifiée (borg check)
```

### Cycle de restauration — **obligatoire**

```
[ ] J'ai identifié une sauvegarde précise
[ ] Le format est exploitable
[ ] Les données attendues sont présentes
[ ] La restauration a été exécutée dans un environnement de test
[ ] Le contenu restauré est identique à l'original (SHA256)
[ ] La procédure de récupération est écrite
[ ] Ce qui n'a pas été testé est noté
```

> Une sauvegarde non restaurée reste une **hypothèse opérationnelle**.

---

## 6. Automatisation

*Partie II § 8 — automatiser sans perdre le contrôle*

```
[ ] La procédure manuelle est écrite AVANT le script
[ ] Le script est lisible sans le lire ligne à ligne
[ ] Les entrées sont validées (types, plages, formats)
[ ] Les dépendances sont vérifiées au démarrage
[ ] Les erreurs sont interceptées (set -euo pipefail)
[ ] Le script est relançable sans conséquence double (flock si nécessaire)
[ ] La sortie est prévisible et exploitable
[ ] Le script peut être exécuté par une autre personne
[ ] La syntaxe est vérifiée (bash -n / shellcheck)
```

---

## 7. Revue de code

*Partie VI § 27 — revue par les pairs*

Pour chaque solution présentée, vérifier :

```
[ ] Quel problème ce choix résout-il ?
[ ] Sur quelles hypothèses repose-t-il ?
[ ] Quelles dépendances introduit-il ?
[ ] Quel est son coût de maintenance ?
[ ] Quels tests le couvrent ?
[ ] Quelle preuve d'exécution existe-t-il ?
[ ] Le comportement est-il reproductible ?
[ ] Qu'est-ce qui n'a pas encore été testé ?
[ ] Quelle limite est assumée ?
```

**Question centrale à poser :** « Qu'est-ce qui vous permet d'affirmer cela ? »

---

## 8. Passation

*Partie V § 23 — le travail est-il transmissible ?*

```
[ ] Objectif du système
[ ] Architecture et composants
[ ] Prérequis et dépendances
[ ] Procédure d'installation
[ ] Configuration importante
[ ] Vérifications à faire après intervention
[ ] Points de surveillance
[ ] Procédure de sauvegarde et de restauration
[ ] Incidents connus et leurs causes
[ ] Limites explicites
[ ] Point de contact ou procédure d'escalade
```

> **Test final :** une personne sans mémoire du projet doit pouvoir reprendre le
> travail avec cette documentation seule. Si ce n'est pas le cas, la
> documentation est incomplète — pas la personne.

---

## 9. Préparation d'une démonstration

*Partie IV § 26, Partie V § 12*

```
[ ] Objectif énoncé en une phrase
[ ] Périmètre défini
[ ] État initial documenté
[ ] Préconditions listées
[ ] Ce qui va être montré est identifié (quel artefact, quelle question)
[ ] Le critère de réussite est explicite
[ ] La limite est préparée et assumée
[ ] La preuve est disponible et lisible
```

**Durée à tenir :** 3 à 5 minutes. Au-delà, ce n'est plus une démonstration.

---

## 10. Contrôle final d'une compétence

*Partie IV § 37 — cinq questions*

Une compétence peut être déclarée vérifiée uniquement si ces cinq réponses
existent :

```
[ ] 1 · Qu'est-ce qui devait être démontré ?
[ ] 2 · Dans quel environnement ?
[ ] 3 · Qu'est-ce qui a réellement été exécuté ?
[ ] 4 · Comment le résultat a-t-il été vérifié ?
[ ] 5 · Quelles sont les limites de la preuve ?
```

Si une seule réponse manque, la compétence reste **DÉCLARÉ** ou **NON ÉTABLI**.

---

## 11. Contrôle d'un livrable éditorial

*Spécifique au travail sur ce livre — contrôlé lors de la rédaction des parties 03 à 06*

```
[ ] Aucun mot parasite non français dans le texte
[ ] Les canevas sont alignés (espaces avant « : »)
[ ] Aucun chiffre sans la commande qui l'a produit
[ ] Aucun statut déclaré sans sa preuve
[ ] Les renvois entre parties sont présents
[ ] Les fichiers modifiés sont dans le périmètre annoncé
```

---

## 12. Auto-évaluation après simulation

*Partie VI § 31*

À remplir **immédiatement** après l'exercice, avant d'en oublier le détail :

```
[ ] Ce que j'ai réussi
[ ] Ce que j'ai observé
[ ] Ce que j'ai vérifié
[ ] Ce qui a échoué
[ ] Ce que je n'ai pas pu établir
[ ] Ce que je ferais différemment
[ ] Ce que je dois encore apprendre
```

Une difficulté non transformée en action d'apprentissage risque de se répéter.
Une action sans preuve risque de rester une intention.
