# Plan de capacité à 36 mois

**Point de départ** : RAM et stockage dimensionnés en A1 *(valeurs ci-dessous à figer une fois le tableau de dimensionnement finalisé — hypothèses provisoires)*.

**Hypothèses** : RAM_0 = 96 Go utiles · Stockage utile = 1,5 To · croissance 15 %/an.

| Année | RAM (×1,15ⁿ) | % de RAM_0 | Seuil | Décision déclenchée |
| --- | --- | --- | --- | --- |
| N+0 | 96 Go | 100 % référence | — | point zéro |
| N+1 | 110,4 Go | 115 % | < 70 % de la cible | surveillance |
| N+2 | 127,0 Go | 132 % | **~70 % de la RAM physique si 192 Go** | **alerte** : étude d'extension |
| N+3 | 146,0 Go | 152 % | **~80 %** | **commande** : +32 Go (délai fournisseur 6 semaines) |

| Année | Stockage utile | % de la baie (2,4 To utiles RAID 10) | Décision |
| --- | --- | --- | --- |
| N+0 | 1,5 To | 62 % | référence |
| N+1 | 1,73 To | 72 % | alerte — purge des snapshots anciens |
| N+2 | 1,98 To | 83 % | **commande** de disques (extension baie) |
| N+3 | 2,28 To | 95 % | **critique** — interdit (règle des 80 % max respectée grâce à la commande N+2) |

**Seuils formalisés** : alerte 70 % · commande 80 % · critique 90 %. La commande se déclenche à 80 % **moins le délai d'approvisionnement** (6 semaines) — c'est le cœur de la gestion de capacité.

**Calendrier des mises à jour** :
- **Mensuel** : correctifs de sécurité (OS, pare-feu, hyperviseur) — RFC « standard » ;
- **Trimestriel** : montées de version mineures (RFC « normal », passage CAB) ;
- **Annuel** : révision du plan de capacité, test PRA, revue des accès.

**Budget indicatif (PME, à ajuster)** : extensions RAM/disques (N+2/N+3), licences (Windows Server AD, éventuel outil de sauvegarde pro), contrats de support, formation admin, lien de secours WAN (4G/5G). *Le lab démontre que la partie logicielle (pare-feu, hyperviseur, sauvegarde, stockage) est à 0 € de licence — le budget porte sur le matériel et le support.*
