# Objectifs à compléter

Ce fichier recense ce qui **n'est pas démontré** dans le dossier de référence et
qui constitue un travail de professionnalisation à produire.

Il n'est pas une liste de défauts. C'est une **feuille de route**.

**Convention de statut :** ce fichier ne traite que les lignes **OBJECTIF**, **DÉCLARÉ**
promu à chantier, et **NON ÉTABLI** — les trois statuts qui impliquent un travail
restant. Les lignes **DÉMONTRÉ** et **INTERPRÉTÉ** relèvent de la matrice et n'ont
pas leur place ici. Aucune ligne de cette annexe ne doit être reformulée en
compétence acquise. Si une preuve est
produite, la ligne correspondante de [`MATRICE_PREUVES.md`](./MATRICE_PREUVES.md)
change de statut — et cette annexe est mise à jour.

---

## 1. Les lignes en attente, par priorité

La priorisation vient du rapport effort / valeur démontrable, pas de
l'importance théorique.

### Priorité 1 — Docker / Compose

**Statut actuel : DÉCLARÉ** — un `docker-compose.yml` de 281 lignes, 8 services,
3 réseaux, validé par une étape de CI. Aucune exécution observée.

**Ce qui manque :** une preuve d'exécution et de fonctionnement.

**Action :**

```bash
docker compose config --quiet          # validation
docker compose up -d                   # démarrage
docker compose ps                      # état
docker inspect <service>               # détail
docker compose logs --tail 50 <service>
```

**Preuve attendue :** sortie de `docker ps` et d'un `docker inspect`, avec la date
et l'hôte.

**Effort : faible.** Docker est présent, la configuration est écrite. C'est le
meilleur rapport effort/valeur du dossier.

---

### Priorité 2 — Scripting Bash

**Statut actuel : DÉCLARÉ** — 15 scripts, 4 014 lignes, `bash -n` 15/15,
`set -euo pipefail` 15/15. Aucune exécution.

**Ce qui manque :** une exécution réelle sur cette machine ou sur une cible
identifiée.

**Action :** exécuter un script en lecture seule (`sys_info.sh`), conserver la
sortie et le journal syslog.

**Preuve attendue :** sortie de la commande + entrée syslog correspondante.

**Réserve à documenter :** le mécanisme d'élévation des scripts manipulant `/etc`
n'est pas établi (`sudo` n'apparaît que dans un script sur quinze).

---

### Priorité 3 — Sauvegarde / PRA BorgBackup

**Statut actuel : DÉCLARÉ** — rétention 7/4/12, script de restauration avec
comparaison SHA256. Aucune exécution observée.

**Ce qui manque :** un cycle sauvegarde + restauration exécuté.

**Action :** créer un dépôt de test, `borg create`, `borg list`, puis
`restore_test.sh` sur une donnée témoin.

**Preuve attendue :** journal du test de restauration réussi, avec la comparaison
des sommes de contrôle.

**Réserve à documenter :** le README du projet affirme « 130 assertions » validées
en banc d'essai. **Aucun harnais de test n'existe dans le dépôt** — cette
affirmation reste non démontrée.

---

### Priorité 4 — Géospatial Offline

**Statut actuel : DÉCLARÉ** — 5 modules Python géospatiaux, écriture GeoPackage
conforme (`gpkg_contents`, `gpkg_spatial_ref_sys`), lecteur MBTiles. **Aucune
source Android** : 0 fichier `.kt`, 0 `.java`, 0 `AndroidManifest.xml`. Les trois
documents de `docs/` sont à 0 octet.

**Ce qui manque :** plusieurs maillons, tous non franchis.

**Action, dans l'ordre :**

1. `python3 app/main.py --self-test` — valider la chaîne Python sans GPS ni réseau
2. Produire un GeoPackage et l'ouvrir dans un SIG tiers
3. Vérifier la compatibilité Chaquopy / AGP 8.7.3 (non établie)
4. Construire l'APK (maillon jamais atteint)

**Preuve attendue, par étape :** sortie conservée et datée.

**Réserve à documenter :** les 5 dépendances déclarées dans `requirements.txt`
(`geopandas`, `shapely`, `pysqlite3`, `requests`, `pydantic`) ne sont importées par
aucun module. Leur présence au build n'est pas anodine ; leur disponibilité en
roulette arm64 Python 3.10 n'est pas établie.

---

## 2. Lignes sans artefact exploitable

### Virtualisation KVM/QEMU

**Statut actuel : OBJECTIF** — aucun artefact dans le dossier. Une fiche de
révision de 228 lignes existe, ce n'est pas une preuve.

**Action :** créer une VM, snapshot, sauvegarde, restauration ; conserver les
sorties.

---

### Services Web, Mail, VoIP, DNS

**Statut actuel : NON ÉTABLI** — c'est la lacune la plus concrète du dossier.

Une unité `systemd` lance Chromium vers `http://127.0.0.1:8080/`, mais **aucun
artefact du dépôt ne fournit ce serveur**. Ni configuration nginx, ni lighttpd, ni
service équivalent.

Deux voies possibles, à trancher explicitement :

| Voie | Conséquence |
|---|---|
| **Livrer la configuration** du serveur du port 8080 dans le dépôt | Le projet devient reproductible de bout en bout |
| **Documenter la décision** que ce serveur relève de l'opérateur du déploiement | Le projet assume une dépendance externe, et le dit |

**Action :** choisir une voie, puis l'appliquer.

**Mail et VoIP :** mentionnés dans un README, aucun artefact. Ne pas les présenter
comme traités.

---

### Admin Linux en production

**Statut actuel : NON ÉTABLI** — des scripts existent et manipulent `/etc` et
`/run`, mais aucun mécanisme d'élévation n'est établi pour treize scripts sur
quinze.

**Ce qui manque :** établir et documenter le modèle de privilèges — exécution en
root, `sudo` avec fichier de règles, ou compte de service dédié.

---

### Anglais technique et veille

**Statut actuel : OBJECTIF** — aucun artefact.

**Action possible :** produire une note de veille mensuelle archivée, et une
synthèse rédigée en anglais d'une documentation technique.

---

## 3. Domaines du référentiel sans pratique documentée

Ces domaines figurent dans le plan de formation mais **n'ont aucun artefact**.
Ils restent des objectifs de professionnalisation, jamais des compétences.

| Domaine | Statut |
|---|---|
| Windows Server | OBJECTIF |
| Active Directory | OBJECTIF |
| Virtualisation avancée (VMware, Hyper-V) | OBJECTIF |
| SAN / NAS / RAID | OBJECTIF |
| Normes et référentiels (ISO 27001, RGPD) | OBJECTIF |
| ITIL et méthodes de travail | OBJECTIF |
| Leadership et gestion d'équipe | OBJECTIF |
| Gestion budgétaire | OBJECTIF |

La formulation correcte est :

> « Ces domaines font partie de mon plan de professionnalisation et je dois encore
> produire les pratiques et preuves correspondantes. »

---

## 4. Ce qui ne doit jamais être fait pour « compléter »

Cette annexe existe pour être remplie **par des preuves**, jamais par des
formulations.

À ne pas faire :

- rédiger une compétence sans l'avoir exercée ;
- qualifier une pratique de « production » sans capture d'un environnement réel ;
- convertir un objectif en acquis dans la matrice pour « équilibrer » un tableau ;
- présenter une documentation comme une exécution ;
- supprimer une lacune pour améliorer l'apparence d'un dossier.

---

## 5. Suivi

| Champ | Contenu |
|---|---|
| Objectif ouvert au lancement | `N.D.` |
| Nombre de lignes à clôturer | 7 |
| Priorité du prochain chantier | `N.D.` |
| Date de mise à jour | `N.D.` |

Ces trois champs se remplissent à chaque nouveau chantier prouvé, en même temps
que la mise à jour de la matrice.
