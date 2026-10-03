# Matrice des preuves

Annexe structurante du livre. Elle relie les compétences visées par le poste
d'IT Officer, les artefacts réellement présents dans le dossier, le statut que
l'on peut honnêtement leur attribuer, et la formulation autorisée en entretien.

---

## Comment lire cette matrice

Chaque ligne suit la chaîne de qualification :

```
COMPÉTENCE
    ↓
SOURCE IDENTIFIÉE ?
    ↓
OBSERVABLE PRÉCIS ?
    ↓
PREUVE D'EXÉCUTION ?
    ↓
STATUT
    ↓
FORMULATION AUTORISÉE EN ENTRETIEN
```

**Un artefact n'est pas automatiquement une preuve de compétence.** Un fichier
existe ; ce qu'il démontre dépend de ce qui a été exécuté, observé ou mesuré.

---

## Les cinq statuts

| Statut | Signification | Ce que l'on peut en dire |
|--------|---------------|---------------------------|
| **DÉMONTRÉ** | Une preuve vérifiable, issue d'une exécution constatée, établit le résultat ou la compétence dans le périmètre considéré. Un artefact non exécuté n'atteint jamais ce statut : il reste DÉCLARÉ. | « Je l'ai fait et voici la preuve » |
| **DÉCLARÉ** | La documentation affirme ; l'exécution n'a pas été observée | « C'est ce que j'ai écrit ; je ne l'ai pas exécuté en production » |
| **INTERPRÉTÉ** | Une déduction à partir de plusieurs observations | « On peut en déduire que… » — jamais comme un fait |
| **OBJECTIF** | Pas d'artefact ; c'est une cible d'apprentissage | « C'est ce que je travaille » |
| **NON ÉTABLI** | Une affirmation existe mais n'a pas pu être vérifiée | « Je n'ai pas de preuve de cela. » |

---

## Point de départ

> Les audits de Phase A établissent l'existence et certaines caractéristiques
> des artefacts, mais **aucune compétence opérationnelle n'est qualifiée
> DÉMONTRÉE sur la seule base de ces audits**. La production ou l'exécution d'une
> preuve supplémentaire sera nécessaire pour faire évoluer un statut.

Cette situation n'est pas anormale : un dossier de projet montre ce qui a été
écrit, pas ce qui a été exercé en exploitation. C'est précisément ce que la
matrice sert à rendre visible.

---

## Matrice

| # | Compétence | Source | Observable | Statut | Preuve attendue | Usage entretien |
|---|------------|--------|-----------|--------|-----------------|-----------------|
| 1 | Admin Linux prod Debian/Ubuntu | `git_workspace/scripts-admin/` (15 scripts) · `git_workspace/infra-as-code/ansible/roles/common/tasks/main.yml` (42 l.) | Scripts manipulant `/etc`, `/run`, `/var/backups`. Rôle `common` installe `ca-certificates`, `chrony`, `curl`, `jq`. Mécanisme d'élévation des scripts non établi (sudo présent dans 1 script sur 15). | **NON ÉTABLI** | Exécution sur machine réelle, capture `journalctl`, preuve d'élévation réussie pour un script manipulant `/etc`. | « J'ai écrit 15 scripts d'administration ; je n'ai pas encore la démonstration de leur exécution sur un serveur en production. » |
| 2 | Virtualisation KVM/QEMU | Aucune source. `prep_entretien/tutorial/02_MAITRISE_TECHNIQUE/fiches_techniques/fiche_kvm.md` (228 l.) est un document de révision, pas un artefact. | Aucun artefact KVM dans le dossier. | **OBJECTIF** | Lab : créer une VM, snapshot, sauvegarde, restauration ; conserver les sorties. | « C'est mon premier chantier de production de preuve. » |
| 3 | Docker/Compose prod | `git_workspace/infra-as-code/docker-compose.yml` (281 l.) · services aux lignes 20, 53, 78, 103, 145, 173, 207, 239 · `git_workspace/scripts-admin/` (deploy_service.sh, healthcheck_all.sh) | 8 services déclarés, 3 réseaux, `data` en `internal: true`, `no-new-privileges` sur 8/8. Validation par `docker compose config -q` définie en CI (`.github/workflows/ci.yml`). **Aucune exécution n'a été observée.** | **DÉCLARÉ** | `docker compose config` réel, `docker compose up` sur un hôte, `docker ps`, `docker inspect` d'un service, logs de démarrage. | « Le stack est écrit et validé statiquement ; je ne l'ai pas encore porté sur un hôte de production. » |
| 4 | Réseau : VLAN, VPN, DNS, FW | `git_workspace/scripts-admin/network/` (dns_verify.sh 237 l., vlan_check.sh 279 l., wg_watchdog.sh 281 l.) · `git_workspace/infra-as-code/docker-compose.yml` — service `wireguard` l. 207–234 | 3 scripts réseau substantiels. WireGuard déclaré en Compose avec `NET_ADMIN`. Le rôle `security` installe `nftables` mais **aucune règle nftables n'est livrée**. | **DÉCLARÉ** | Capture de `wg show`, résolution DNS réelle, sortie de `ip -br link` sur VLAN configuré. | « Le diagnostic réseau est écrit ; l'installation effective d'une segmentation VLAN reste à prouver. » |
| 5 | Sécurité : durcissement, secrets, audit | `git_workspace/infra-as-code/ansible/roles/security/tasks/main.yml` (54 l.) · `git_workspace/scripts-admin/security/` (lynis_audit.sh 182 l., vault_rotate.sh 260 l., wg_key_rotate.sh 255 l.) · `git_workspace/infra-as-code/vault/config/vault.hcl` | Sysctl de durcissement kernel, fail2ban, `auditd`, `sshd` (opt-in). `vault.hcl` porte `tls_disable = 1` et `disable_mlock = true` — à corriger avant tout usage réel. `ansible/vault.yml` : **0 octet**. | **DÉCLARÉ** | Rapport Lynis réel, sortie `sshd -T`, rotation de clé exécutée, correction du TLS Vault. | « Le durcissement est écrit ; Vault n'est pas encore configuré en TLS et je le dis. » |
| 6 | Supervision Zabbix/Grafana/Netdata/Prometheus | `git_workspace/infra-as-code/docker-compose.yml` l. 78, 103, 145, 173 · `monitoring/prometheus.yml` · `monitoring/prometheus.rules.yml` (56 l.) | 4 services de supervision déclarés, scrape de 4 cibles. Dashboards Grafana et templates Zabbix : `.gitkeep` seuls, **vides**. | **DÉCLARÉ** | Capture Grafana/Zabbix avec métriques réelles, test d'une règle d'alerte, `alerts` Prometheus non vides. | « La supervision est déclarée ; les dashboards ne sont pas encore produits, c'est un chantier identifié. » |
| 7 | Sauvegarde / PRA BorgBackup 3-2-1 | `git_workspace/scripts-admin/backup/` (borg_backup.sh 277 l., borg_restore_test.sh 293 l.) · rétention l. 14–16 : 7/4/12 | Scripts de sauvegarde et de test de restauration avec comparaison SHA256. Aucune exécution observée. README `infra-as-code` affirme « 130 assertions » : **aucun harnais dans le dépôt**. | **DÉCLARÉ** | Réel `borg create`, `borg list`, `borg check`, journal d'un `restore_test.sh` réussi. | « Le dispositif 3-2-1 est écrit avec rétention 7/4/12 ; je n'ai pas de trace d'une restauration réellement réussie. » |
| 8 | Scripting Bash/Python/Cron/Git | `git_workspace/scripts-admin/` (15 scripts, 4 014 lignes, `set -euo pipefail` 15/15) · `git_workspace/geo-android-offline/app/` (5 modules Python, syntaxe valide 5/5) · `git_workspace/pi-kiosk-offline/sync_daemon.py` (581 l.) · `git_workspace/infra-as-code/scripts/` (5 scripts) | Discipline statique homogène : `usage()` 15/15, `logger` 15/15, `bash -n` 15/15. Robustesse comportementale **non établie** (aucune exécution). | **DÉCLARÉ** | Sortie de `bash -x` sur un script, `shellcheck` sans avertissement, journal syslog réel, `py_compile` sans écriture. | « J'ai écrit 4 014 lignes de scripts avec discipline stricte ; je n'ai pas de banc d'essai qui le démontre encore. » |
| 9 | Géospatial Offline Android/GeoPackage | `git_workspace/geo-android-offline/app/` (5 modules) · `geopackage_writer.py` (7 371 o., crée `gpkg_contents` et `gpkg_spatial_ref_sys`) · `mbtiles_utils.py` (lecteur MBTiles) · `build.gradle.kts` (51 l.) | **0 fichier Kotlin, 0 Java, 0 XML, 0 AndroidManifest**. `docs/` : 3 fichiers à **0 octet**. 5 dépendances `requirements.txt` déclarées, **0 importée** par le code. | **DÉCLARÉ** | APK construit et lancé ; `--self-test` exécuté avec sortie ; GeoPackage ouvert dans un SIG tiers. | « Les modules Python géospatiaux sont écrits ; l'application Android n'existe pas encore. » |
| 10 | Services : Web, Mail, VoIP, DNS | `git_workspace/pi-kiosk-offline/kiosk.service` l. 22–25 : Chromium → `http://127.0.0.1:8080/` · `git_workspace/infra-as-code/docker-compose.yml` — Nginx Proxy Manager l. 53 | `kiosk.service` consomme un serveur HTTP **qu'aucun artefact du dépôt ne livre**. Mail et VoIP : mentionnés dans le README `infra-as-code`, **aucun artefact**. | **NON ÉTABLI** | Fournir la configuration du serveur web du port 8080 ; démonstration d'un service mail. | « J'ai conçu un service qui dépend d'un serveur web que je n'ai pas encore fourni — c'est un écart que j'ai identifié moi-même. » |
| 11 | Support / Pédagogie / Doc | 56 fichiers `.md` dans `/home/betsa/dossier_pret/` (322 Ko) · `git_workspace/infra-as-code/docs/` (46 907 o., 5 fichiers non vides) | Volume documentaire substantiel. Mais 4 fichiers de `git_workspace/*/docs/` sont à **0 octet** et 3 READMEs font 4 lignes. | **DÉCLARÉ** | Un document a été relu par un tiers ; version publiée accessible. | « Je documente ; la relecture externe et la publication ne sont pas encore faites. » |
| 12 | Anglais technique / Veille | Aucune source identifiée dans le dossier. | Aucun artefact. | **OBJECTIF** | Note de veille rédigée et archivée ; lecture d'une documentation Anglaise synthétisée. | « C'est un objectif : je n'ai pas encore produit de trace de veille. » |

---

## Récapitulatif des statuts

```
DÉMONTRÉ     0
DÉCLARÉ      8   (3, 4, 5, 6, 7, 8, 9, 11)
INTERPRÉTÉ   0
OBJECTIF     2   (2, 12)
NON ÉTABLI   2   (1, 10)
──────────────────────
Total       12
```

*(La colonne « Usage entretien » contient des formulations en français ; toute
citation directe dans un entretien anglais devra être reformulée.)*

---

## Ce que la matrice ne dit pas

Elle ne dit pas que le travail est mauvais. Elle dit que **le dossier contient
des artefacts, pas encore des preuves d'exécution**.

Trois exemples du même écart, relevés lors des audits de Phase A :

| Projet | Artefact | Ce qui manque |
|--------|----------|---------------|
| `infra-as-code` | `site.yml` + 6 rôles rédigés | Inventaire de production vide (`.gitkeep` seul) → aucune cible pour `ansible-playbook` |
| `geo-android-offline` | `build.gradle.kts` configure Chaquopy | 0 source Android ; l'APK n'a jamais été construit |
| `pi-kiosk-offline` | `kiosk.service` lance Chromium | Le serveur HTTP du port 8080 n'est fourni par aucun artefact |

---

## Premiers chantiers de production de preuve

Par ordre de rapport effort / valeur démontrable :

1. **Composer 3** — `docker compose config -q` puis `docker compose up -d`, capture `docker ps`. Transforme une ligne DÉCLARÉ en DÉMONTRÉ à faible coût.
2. **Scripting 8** — exécuter `sys_info.sh` puis `healthcheck_full.sh` en lecture seule sur cette machine, conserver la sortie et le journal syslog.
3. **Sauvegarde 7** — un cycle `borg create` + `borg list` sur un dépôt de test.
4. **Géospatial 9** — exécuter `main.py --self-test`, conserver la sortie.
5. **Services 10** — décider et livrer la configuration du port 8080, ou documenter la décision.

---

## Règle de mise à jour

Une ligne ne change de statut que si :

- une **preuve d'exécution** est produite et conservée, ou
- une **relecture des sources** établit un fait nouveau.

Passer de DÉCLARÉ à DÉMONTRÉ exige un artefact d'exécution, pas un
argumentaire.
