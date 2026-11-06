# Procès-verbal du CAB

**Réunion** : mardi 03/11/2026, 17h30 — Comité consultatif des changements (CAB)
**Présents** (jeu de rôle) :

| Rôle | Personne | Position |
| --- | --- | --- |
| Demandeur | admin infra : Anto, Yohann, Justin, Ryan | présente la RFC |
| RSSI | H. Lambert | évalue le risque sécurité |
| Exploitant | M. Dubois | exécutera la mise à jour |
| Président | S. Kern (DSI) | arbitre |

**Déroulé** :
1. Présentation de la RFC-001 (impact, plan de test, retour arrière) ;
2. Questions du RSSI : *et si la nouvelle version réécrivait le format des règles NAT ?* → Réponse : restauration du `config.xml` testée + snapshot intégral ; risque résiduel accepté ;
3. Question de l'exploitant : *faut-il prévenir les métiers ?* → Oui : information simple (coupe-feu de 10 min vendredi soir), envoyée par le président ;
4. Question du président sur le délai : accord sur 30 minutes max, retour arrière automatique.

**Décision** : **approuvée** aux conditions de la RFC-001 (snapshot et export avant, tests après, 30 min max).
**Suivi** : PV + résultats de tests versés dans `infra-lab/gouvernance/` ; la RFC passe au statut « réalisée » après tests conformes.