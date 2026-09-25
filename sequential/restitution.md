## Décision ayant fait l'objet de discussions (Modèle séquentiel)

Lors de la modélisation séquentielle, l'équipe s'est interrogée sur la granularité du "Système" :
* **Option A** : Découper le système en plusieurs objets techniques (ex: `InterfaceWeb`, `ContrôleurRéservation`, `BaseDeDonnées`).
* **Option B** : Représenter le système comme une seule entité "boîte noire" (Diagramme de Séquence Système - DSS).

---

## Choix retenu et justification

Nous avons opté pour l'**Option B (Le Système comme entité unique)**.

### Raisons de ce choix :
1. **Cohérence avec l'étape d'analyse** : Nous traduisons directement les fiches de cas d'utilisation réalisées le matin. Le but actuel est de valider la logique métier avec le gérant (vérifier les règles des arrhes de 10% ou les calculs de consommation), et non l'architecture logicielle interne.
2. **Lisibilité** : Modéliser la base de données et l'IHM aurait surchargé les diagrammes. En gardant le "Système" unifié, nous mettons en évidence les interactions cruciales avec les systèmes externes (comme le **Service de paiement**).