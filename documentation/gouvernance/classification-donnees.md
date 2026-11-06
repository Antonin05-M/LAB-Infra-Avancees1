# Classification et politique d'accès


| Niveau | Exemples NovaTech | Groupes (ACL) | Conservation | Exigences |
| --- | --- | --- | --- | --- |
| **Public** | Site web vitrine, offres commerciales | — | illimitée | Aucune |
| **Interne** | Messagerie, procédures internes, GED générale | grp-collab-rw / -ro | 1–3 ans selon type | Accès authentifié, accès nominal |
| **Confidentiel** | Données ERP/compta, dossiers clients, config infra | grp-compta-rw, grp-compta-ro, grp-it-rw | 10 ans (obligations) | ACL strictes, journalisation des accès (auditd), chiffrement au repos |
| **Secret** | Données RH, paie, credentials/secrets | grp-rh-rw, grp-rh-ro | durée légale | + chiffrement obligatoire (LUKS/ZFS), accès nominatif tracé, revue mensuelle |

**Politique d'accès (moindre privilège)** :
1. Un utilisateur = un compte **nominal** ; aucun compte partagé ;
2. Accès par **groupes métier** uniquement (jamais par utilisateur directement) ;
3. Le schéma `rw`/`ro` distingue lecture et écriture par métier ;
4. Revue **trimestrielle** des ACL (liée aux vérifications `getfacl` de l'atelier A8) ;
5. Départ/mutation : le RH déclenche la révocation sous 24 h (entrée RACI §6) ;
6. Accès administrateur **uniquement via le bastion** (SSH, clé, source restreinte) ;
7. Tout accès aux données Confidentiel+ est journalisé (auditd, A11).