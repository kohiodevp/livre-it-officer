# Référentiel de commandes

Annexe pratique du livre. Elle regroupe les commandes utilisées tout au long des
parties, classées par usage.

**Convention de statut :** une commande listée ici est un **outil documenté**, pas
une compétence acquise. La compétence correspondante reste à qualifier dans
[`MATRICE_PREUVES.md`](./MATRICE_PREUVES.md).

**Avertissement :** aucune commande de cette annexe n'a été exécutée sur votre
machine. Elles sont données comme aide-mémoire, à vérifier dans un environnement
maîtrisé.

---

## 1. Identification du système

*Partie II § 3.1 — navigation et identification*

| Besoin | Commande | Ce qu'elle établit |
|---|---|---|
| Version du noyau | `uname -a` | le noyau et l'architecture |
| Distribution et version | `cat /etc/os-release` | la distribution |
| Identité | `id` | l'utilisateur courant et ses groupes |
| Répertoire courant | `pwd` | l'emplacement de travail |
| Arborescence | `ls -la` | le contenu d'un répertoire |
| Taille d'un répertoire | `du -sh <chemin>` | l'espace occupé |
| Ressources mémoire | `free -h` | la mémoire disponible |
| Charge et cœurs | `uptime`, `nproc` | la charge système et le nombre de cœurs |
| Espace disque | `df -h` | l'espace disponible par système de fichiers |

---

## 2. Fichiers, permissions, processus

*Partie II § 3.2, § 4*

| Besoin | Commande | Ce qu'elle établit |
|---|---|---|
| Permissions | `ls -l` | propriétaire, groupe, droits |
| Lien symbolique | `ls -ld` | le type de l'entrée |
| Détenteur réel du fichier | `stat -c '%U %G %a' <fichier>` | l'UID et le GID effectifs |
| Modifier les droits | `chmod 0640 <fichier>` | les permissions |
| Changer le groupe | `chgrp <groupe> <fichier>` | le groupe propriétaire |
| Processus en cours | `ps aux` | les processus actifs |
| Filtrer un processus | `pgrep -a <nom>` | un processus précis |
| Tuer un processus | `kill <pid>` puis `kill -9 <pid>` | l'arrêt d'un processus |

---

## 3. Services

*Partie II § 4 — démarrer n'est pas fonctionner*

La chaîne de vérification complète :

| Niveau | Commande | Ce qu'elle établit |
|---|---|---|
| 1 · Le service existe | `systemctl list-unit-files --type=service` | le service est installé |
| 2 · Le service est actif | `systemctl status <service>` | l'état courant |
| 3 · Le port écoute | `ss -tlnp` | les ports en écoute |
| 4 · Le protocole répond | `curl -I http://127.0.0.1:<port>` | une réponse HTTP |
| 5 · La réponse est correcte | `curl -s http://…` puis comparaison | le comportement attendu |
| 6 · Les journaux sont propres | `journalctl -u <service> -n 50 --no-pager` | absence d'erreur bloquante |

```bash
# Démarrage et activation
systemctl start <service>
systemctl enable <service>
systemctl reload <service>

# Diagnostic
journalctl -u <service> -f          # suivi en direct
journalctl -u <service> --since "1 hour ago"
```

**Règle.** Ne jamais conclure « fonctionnel » sur le seul résultat de
`systemctl status`. Les six niveaux sont cumulatifs.

---

## 4. Réseau

*Partie II § 5, Partie III § 13*

La chaîne de diagnostic, dans l'ordre :

| Étape | Commande | Ce qu'elle établit |
|---|---|---|
| Interface | `ip -br link` | l'état de l'interface (UP / DOWN) |
| Adressage | `ip -br addr` | les adresses configurées |
| Route | `ip route` | la route par défaut |
| Résolution | `dig <nom>` | l'adresse retournée |
| Résolution inverse | `dig -x <ip>` | le PTR |
| Connectivité | `ping -c 3 <cible>` | l'accessibilité IP |
| Port | `nc -zv <cible> <port>` | l'ouverture du port |
| Service | `ss -tlnp` | le processus qui écoute |

```bash
# Interface WireGuard
wg show                          # état des interfaces et handshake
wg show <if> latest-handshakes # dernière negotiation

# VLAN
ip -d link show <if>            # détail tag VLAN
bridge vlan show               # table de correspondance
```

---

## 5. Ressources et diagnostic

*Partie III § 9, § 10, § 24*

| Besoin | Commande | Ce qu'elle établit |
|---|---|---|
| Mémoire | `free -h` | disponible vs utilisé |
| Processeurs gourmands | `ps aux --sort=-%mem | head` | les premiers consommateurs |
| Charge | `uptime` | moyenne sur 1, 5, 15 min |
| Inodes | `df -i` | consommation d'inodes |
| Fichiers volumineux | `du -h <chemin> | sort -rh | head` | les plus gros éléments |
| Journaux | `journalctl -p err -n 50 --no-pager` | les erreurs récentes |
| Fichiers modifiés récemment | `find <chemin> -mtime -1` | ce qui a changé |

**Règle.** « La machine manque de mémoire » est une conclusion. Elle nécessite la
mesure **et** l'identification des consommateurs avant d'être énoncée.

---

## 6. Sauvegarde et restauration

*Partie II § 7.2, Partie III § 21*

```bash
# Cycles de sauvegarde (BorgBackup)
borg init --encryption=repokey-blake2 <repo>
borg create --stats <repo>::<prefixe>-<date> /etc /opt
borg list <repo>
borg check <repo>

# Test de restauration
# L'extraction se fait dans le RÉPERTOIRE COURANT.
# Pour restaurer ailleurs, on s'y place d'abord.
borg extract --dry-run <repo>::<archive> etc/hostname

mkdir -p <destination>
cd <destination>
borg extract <repo>::<archive> etc/hostname
sha256sum <source> <destination_restauré>   # comparaison
```

**Règle.** Une sauvegarde non restaurée reste une hypothèse opérationnelle. La
preuve est le **résultat de la restauration**, pas l'existence du fichier.

---

## 7. Verrouillage et exécution répétée

*Partie II § 8 — automatiser sans perdre le contrôle*

```bash
# Verrouillage concurrent (évite deux exécutions simultanées)
flock -n /run/lock/mon-script.lock ./mon-script.sh

# Répétition dans une tâche planifiée
*/5 * * * * /usr/local/bin/watchdog.sh    # toutes les 5 min
15 * * * * root /opt/scripts/backup.sh    # chaque heure à H+15
```

**Règle.** Automatiser une procédure mal comprise ne la rend pas plus fiable. Le
script doit être relançable sans conséquence double.

---

## 8. Scripts et qualité statique

*Partie II § 13, § 15*

```bash
# Vérifier la syntaxe sans exécuter le script
bash -n script.sh

# Analyse statique
shellcheck --severity=style script.sh

# Compilation Python sans écrire de fichier
python3 -c "compile(open('module.py').read(), 'module.py', 'exec')"

# Exécution avec trace
bash -x script.sh 2>&1 | tee /tmp/sortie.txt
```

> **Note.** `python3 -m py_compile` crée un `__pycache__/`. Dans un périmètre
> d'audit en lecture seule, préférez la forme `-c "compile(…)"`, qui valide la
> syntaxe sans rien écrire.

---

## 9. Docker et Compose

*Partie II § 9*

```bash
# Validation — sans démarrer de conteneur
docker compose config --quiet

# Cycle complet
docker compose up -d
docker compose ps
docker inspect <service> | grep -A5 '"State"'
docker compose logs --tail 50 <service>
docker compose down
```

| Niveau de l'exercice | Action |
|---|---|
| 1 | `docker run hello-world` |
| 2 | `docker run -e VAR=valeur image` |
| 3 | `docker run -v /hote:/dossier image` |
| 4 | `docker compose up -d` avec deux services |
| 5 | `docker compose exec <service> getent hosts <autre-service>` |
| 6 | `docker compose restart` puis re-vérifier |

**Règle.** `docker compose config -q` valide la syntaxe du fichier. Il ne prouve
ni que les images existent, ni que les services démarrent.

---

## 10. Ansible

*Partie II § 13, Partie VI*

```bash
# Validation statique
ansible-lint ansible/

# Inventaire — sans exécution
ansible-inventory -i ansible/inventories/production --list

# Exécution
ansible-playbook -i ansible/inventories/production ansible/site.yml --check   # dry-run
ansible-playbook -i ansible/inventories/production ansible/site.yml
```

**Prérequis non négociable.** `-i` attend une **source d'inventaire**. La
documentation Ansible accepte un fichier, un répertoire, une URL ou une
liste séparée par des virgules. Un répertoire est donc accepté — mais un
répertoire ne contenant qu'un `.gitkeep` ne fournit aucun hôte : la commande
s'exécute alors sur l'inventaire local vide, et la cible n'est pas atteinte.
C'est un fait, pas une prévision.

---

## 11. Tracer une preuve

*Partie IV § 15*

```bash
# Capturer la date, la commande et sa sortie
{ date -Is; echo "---"; uname -a; } | tee /tmp/preuve-01.txt

# Vérifier le résultat attendu par comparaison
diff <(cat attendu.txt) <(cat obtenu.txt) && echo "conforme"

# Conserver le contexte
git rev-parse HEAD
```

---

## 12. Ce que ce référentiel ne fait pas

Il ne remplace pas `annexes/CHECKLISTS.md` pour la procédure, ni
`annexes/MATRICE_PREUVES.md` pour le statut.

Une commande exécutée ne prouve pas, à elle seule, une compétence : elle prouve
que **cette commande** a produit **ce résultat** dans **cet environnement**.
