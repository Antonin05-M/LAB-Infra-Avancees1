# Registre de risques (EBIOS RM simplifié)

Démarche EBIOS RM réduite : biens essentiels → sources de risque → scénarios → mesures → risque résiduel. **Chaque scénario est relié à un SPOF de l'atelier A1**, et chaque mesure à une démonstration du lab.

| # | Scénario de menace | Bien menacé | SPOF A1 | Mesures (existantes → cibles) | Résiduel |
| --- | --- | --- | --- | --- | --- |
| 1 | Rançongiciel chiffre les serveurs et tente de **détruire les sauvegardes** | Données ERP, fichiers | n°3 (NAS unique) | VLAN sauvegarde isolé, restic append-only + hors-site, LUKS (→ lab A8/A11) | **Moyen** |
| 2 | Panne du lien WAN principal | Tous les services exposés | n°1 (WAN unique) | Double attachement FAI + 4G de secours (dossier) | Faible |
| 3 | Panne du switch cœur | Tous les VLAN | n°2 (switch unique) | Stacking/MLAG + switch de secours (→ lab A10 : bascule VRRP observée) | Faible |
| 4 | Arrêt du serveur ERP (pas de cluster) | Production (commandes, compta) | n°5 (ERP unique) | Redémarrage prioritaire en PRA site distant, RTO/RPO chiffrés (→ lab A11 : mesure réelle du RTO/RPO) | **Moyen** |
| 5 | Coupure du VPN inter-sites | Réplication, sauvegarde hors-site | n°4 (VPN unique) | Second tunnel opérateur alternatif (dossier) | Faible |
| 6 | Compromission du bastion | Accès admin à tout le SI | (design bastion) | Single-homed, DNAT source restreinte, clés SSH uniquement, journalisation OPNsense (→ lab A2) | **Moyen** |
| 7 | Compromission de l'AD (un DC suffit) | Tous les accès, GPO | 2 DC | Deux DC par site, durcissement, MFA admin, sauvegarde system state (dossier) | **Moyen** |

**Lecture pour le jury** : le registre transforme les SPOF de l'A1 en scénarios chiffrables ; les mesures « existantes » sont démontrées dans le lab (VLAN, VRRP, restic, LUKS, auditd), les mesures « cibles » sont argumentées dans le dossier — c'est la boucle complète conception → risque → mesure → preuve.